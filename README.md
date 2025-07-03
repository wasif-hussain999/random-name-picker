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
    const angle = (2 * Math.PI) / numSlices;

    function drawWheel() {
      for (let i = 0; i < numSlices; i++) {
        ctx.beginPath();
        ctx.moveTo(150, 150);
        ctx.fillStyle = `hsl(${i * 360 / numSlices}, 100%, 70%)`;
        ctx.arc(150, 150, 150, i * angle, (i + 1) * angle);
        ctx.lineTo(150, 150);
        ctx.fill();
        ctx.save();
        ctx.translate(150, 150);
        ctx.rotate((i + 0.5) * angle);
        ctx.fillStyle = '#000';
        ctx.fillText(emails[i], 70, 0);
        ctx.restore();
      }
    }

    drawWheel();

    document.getElementById('spin').onclick = function () {
      const randomIndex = Math.floor(Math.random() * emails.length);
      document.getElementById('winner').textContent = `Tag: ${emails[randomIndex]}`;

      this.disabled = true;
      this.textContent = 'Already Generated';
    };
  </script>

</body>
</html>
