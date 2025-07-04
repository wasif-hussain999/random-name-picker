<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Name Picker Wheel</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f3f3f3;
      color: #333;
      padding: 20px;
      text-align: center;
    }
    h1 {
      color: #007BFF;
    }
    #wheel {
      width: 300px;
      height: 300px;
      border-radius: 50%;
      border: 10px solid #333;
      display: block;
      margin: 20px auto;
    }
    #spin {
      margin-top: 10px;
      padding: 10px 20px;
      font-size: 16px;
    }
    #winner {
      font-weight: bold;
      font-size: 18px;
      margin-top: 10px;
    }
  </style>
</head>
<body>

  <h1>Hello!! Motivator</h1>
  <p>Spin the wheel to generate the Name of the next person.</p>
<body>

  <h1>Name Picker Wheel</h1>
  <canvas id="wheel" width="300" height="300"></canvas><br>
  <button id="spin">Spin the Wheel</button>
  <p id="winner"></p>

  <script>
    // Predefined list of all possible names (can be 100+)
    const allNames = [
      'Chirag Dudhrejia',
'Devanshi Kevat',
'Shubham Mishra',
'Jaychan Kumawat',
'Dhruv Shekhat',
'Krusha Panchal',
'Mit Patoliya',
'Divy Kaila',
'Aksh Surani',
'Ikramali Dedhrotiya',
'Falsi Vadaliya',
'Dhruvi Ladani',
'Preksha Pandya',
'Adarsh Adwait',
'Rosalia George',
'Mehul Patel',
'Laxman Deokate',
'Shubhangi Khandar',
'Poras Vyas',
'Manish Patel',
'James Gardner',
'Jalindar Karande',
'Shivangi Bhatt',
'Vishal Vaghasiya',
'Brendon Buthello',
'Nakul Daf',
'Sudhir Patil',
'Honey Chauhan',
'Himanshu Pithadia',
'Srinivas Mothey',
'Parth Pataliya',
'Vishal Katheriya',
'Pinkal Rathod',
'Shreya Tiwari',
'Sumit Thakkar',
'Akshay Vala',
'Asjad Puthawala',
'Ishan Panchal',
'Hetvi Desai',
'Piyush Bidwai',
'Trupti Thakar',
'Kishan Thakkar',
'Ashish Sakhare',
'Sandeep Suthar',
'Sujeet Pawar',
'Yash Upadhyaya',
'Naimish Gohil',
'Nidhi Thakkar',
'Ankit Gupta',
'Bhargav Parmar',
'Krupa Deria',
'Prerna Shelke',
'Simran Ladhani',
'Rahul Pal',
'Gaurang Prajapati',
'Maharshi Shukla',
'Rajan Hansora',
'Anurag Bhuingal',
'Sanny Chauhan',
'Adarsh Mishra',
'Sushilkumar Suthar',
'Vikas Rathod',
'Aliraza Panjwani',
'Akshit Trivedi',
'Hardikkumar Gohel',
'Vaishnavi Bharne',
'Pooja Bagane',
'Rohit Gaddamidi',
'Lusy Patel',
'Mohit Tahiliani',
'Komal Dhokai',
'Ruchit Parmar',
'Pooja Deokate',
'Pradeep Thippani',
'Ankit Shah',
'Ramesh Mokariya',
'Samir Thakkar',
'Jagrut Dave',
'Tarachand Somjani',
'Sagar Gulghane',
'Meet Dalwadi',
'Rohan Lakhani',
'Naresha Bhat',
'Sandesh Gosavi',
'Harshala Kadam',
'Devrajsinh Jadeja',
'Jainam Shah',
'Nutan Jagnade',
'Kinjal Thakkar',
'Trushali Ramoliya',
'Pinkal Panchal',
'Hardik Kher',
'Aakash Thakker',
'Jigar Dabhi',
'Mohit Ingavale',
'Preeti Sharma',
'Suresh  Bavaliya',
'Rajat Sapkal',
'Sanket Jain'
    ];

    // Only 5 names shown on the wheel at a time (rotating subset)
    let visibleNames = [];

    const canvas = document.getElementById('wheel');
    const ctx = canvas.getContext('2d');
    const spinBtn = document.getElementById('spin');
    const winnerText = document.getElementById('winner');

    const sliceCount = 20;
    const anglePerSlice = (2 * Math.PI) / sliceCount;
    let rotation = 0;
    let spinning = false;

    function drawWheel(rotationOffset = 0) {
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      for (let i = 0; i < sliceCount; i++) {
        const startAngle = i * anglePerSlice + rotationOffset;
        const endAngle = startAngle + anglePerSlice;

        ctx.beginPath();
        ctx.moveTo(150, 150);
        ctx.fillStyle = `hsl(${i * 360 / sliceCount}, 100%, 70%)`;
        ctx.arc(150, 150, 150, startAngle, endAngle);
        ctx.lineTo(150, 150);
        ctx.fill();

        // Draw name
        ctx.save();
        ctx.translate(150, 150);
        ctx.rotate(startAngle + anglePerSlice / 2);
        ctx.textAlign = "right";
        ctx.fillStyle = '#000';
        ctx.font = '14px Arial';
        ctx.fillText(visibleNames[i], 140, 5);
        ctx.restore();
      }

      // Center label
      ctx.fillStyle = '#000';
      ctx.font = 'bold 16px Arial';
      ctx.textAlign = 'center';
      ctx.fillText("Who will be", 150, 145);
      ctx.fillText("the next person?", 150, 165);
    }

    function spinWheel() {
      if (spinning) return;

      // Pick a random winner from all names
      const winner = allNames[Math.floor(Math.random() * allNames.length)];

      // Pick 4 more random names to display on the wheel (exclude winner)
      const shuffled = allNames.filter(name => name !== winner)
                               .sort(() => 0.5 - Math.random())
                               .slice(0, 19);

      visibleNames = [...shuffled, winner]
        .sort(() => 0.5 - Math.random()); // Shuffle order on wheel

      drawWheel();

      spinning = true;
      let duration = 4000;
      let start = null;
      let finalRotation = Math.random() * 2 * Math.PI + (10 * 2 * Math.PI);
      let winnerIndex = null;

      function animate(timestamp) {
        if (!start) start = timestamp;
        const elapsed = timestamp - start;

        const progress = Math.min(elapsed / duration, 1);
        rotation = finalRotation * easeOutCubic(progress);
        drawWheel(rotation);

        if (progress < 1) {
          requestAnimationFrame(animate);
        } else {
          spinning = false;

          const normalized = (2 * Math.PI - (rotation % (2 * Math.PI))) % (2 * Math.PI);
          winnerIndex = Math.floor(normalized / anglePerSlice);
          const selectedName = visibleNames[winnerIndex];
          winnerText.textContent = `Tag, you're it: ${selectedName}`;
          spinBtn.disabled = true;
        }
      }

      requestAnimationFrame(animate);
    }

    function easeOutCubic(t) {
      return 1 - Math.pow(1 - t, 3);
    }

    // Initial placeholder names
    visibleNames = ['?', '?', '?', '?', '?','?', '?', '?', '?', '?','?', '?', '?', '?', '?','?', '?', '?', '?', '?'];
    drawWheel();

    spinBtn.onclick = spinWheel;
  </script>

</body>
</html>
