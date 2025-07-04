<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Name Picker Wheel</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f3f3f3;
      color: #999;
      padding: 20px;
    }
    h1 {
      color: #007BFF;
    }
    #wheel {
      width: 300px;
      height: 300px;
      border-radius: 50%;
      border: 10px solid #333;
      position: relative;
    }
    #spin {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 16px;
    }
  </style>
</head>
<body>

  <h1>Hello!! Motivator</h1>
  <p>Spin the wheel to generate the Name of the next person.</p>

  <canvas id="wheel" width="300" height="300"></canvas><br>
  <button id="spin">Generate Now</button>
  <p id="winner"></p>

<script>
  const emails = [   
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

  const canvas = document.getElementById('wheel');
  const ctx = canvas.getContext('2d');
  const numSlices = emails.length;
  const anglePerSlice = (2 * Math.PI) / numSlices;

  let rotation = 0;
  let spinning = false;

  function drawWheel(rotationOffset = 0) {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    for (let i = 0; i < numSlices; i++) {
      const startAngle = i * anglePerSlice + rotationOffset;
      const endAngle = startAngle + anglePerSlice;

      ctx.beginPath();
      ctx.moveTo(150, 150);
      ctx.fillStyle = `hsl(${i * 360 / numSlices}, 100%, 70%)`;
      ctx.arc(150, 150, 150, startAngle, endAngle);
      ctx.lineTo(150, 150);
      ctx.fill();

      // Draw text
      ctx.save();
      ctx.translate(150, 150);
      ctx.rotate(startAngle + anglePerSlice / 2);
      ctx.textAlign = "right";
      ctx.fillStyle = '#000';
      ctx.font = '16px Arial';
      ctx.fillText(emails[i], 140, 5);
      ctx.restore();
    }
  }

  function spinWheel() {
    if (spinning) return;

    spinning = true;
    let duration = 3000; // 3 seconds
    let start = null;
    let finalRotation = Math.random() * 2 * Math.PI + (10 * 2 * Math.PI); // 10 full spins + offset
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

        // Normalize angle to find winning slice
        const normalized = (2 * Math.PI - (rotation % (2 * Math.PI))) % (2 * Math.PI);
        winnerIndex = Math.floor(normalized / anglePerSlice);
        document.getElementById('winner').textContent = `Tag: ${emails[winnerIndex]}`;
        document.getElementById('spin').disabled = true;
        document.getElementById('spin').textContent = 'Already Generated';
      }
    }

    requestAnimationFrame(animate);
  }

  function easeOutCubic(t) {
    return 1 - Math.pow(1 - t, 3);
  }

  drawWheel();

  document.getElementById('spin').onclick = spinWheel;
</script>


</body>
</html>
