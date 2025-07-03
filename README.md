<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My First Web Page</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f3f3f3;
      color: #333;
      padding: 20px;
    }
    h1 {
      color: #007BFF;
    }
  </style>
</head>
<body>
  <h1>Hello!! Motivator</h1>
  <p>Spin the wheel to generate the e-mail id of the next person.</p>
<head>
    <meta charset="UTF-8">
    <title>Generate Button</title>

<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Email Picker Wheel</title>
  <style>
    #wheel {
      width: 300px;
      height: 300px;
      border-radius: 50%;
      border: 10px solid #333;
      position: relative;
    }
    #spin {
      margin-top: 20px;
    }
  </style>
</head>
<body>

<canvas id="wheel" width="300" height="300"></canvas>
<button id="spin">Spin the Wheel</button>
<p id="winner"></p>

<script>
  const emails = [
    'dhruv.shekhat@inferenz.ai',
'krusha.panchal@inferenz.ai',
'mit.patoliya@inferenz.ai',
'divy.kaila@inferenz.ai',
'aksh.surani@inferenz.ai',
'ikramali.dedhrotiya@inferenz.ai',
'falsi.vadaliya@inferenz.ai',
'dhruvi.ladani@inferenz.ai',
'preksha.pandya@inferenz.ai',
'adarsh.adwait@inferenz.ai',
'rosalia.george@inferenz.ai',
'mehul.patel@inferenz.ai',
'laxman.deokate@inferenz.ai',
'shubhangi.khandar@inferenz.ai',
'poras.vyas@inferenz.ai',
'manish.patel@inferenz.ai',
'james.gardner@inferenz.ai',
'jalindar.karande@inferenz.ai',
'shivangi.bhatt@inferenz.ai',
'priyanka.sabharwal@inferenz.ai',
'vishal.vaghasiya@inferenz.ai',
'brendon.buthello@inferenz.ai',
'nakul.daf@inferenz.ai',
'sudhir.patil@inferenz.ai',
'gagandeep.singh@inferenz.ai',
'honey.chauhan@inferenz.ai',
'himanshu.pithadia@inferenz.ai',
'srinivas.mothey@inferenz.ai',
'parth.pataliya@inferenz.ai',
'parth.makwana@inferenz.ai',
'vishal.katheriya@inferenz.ai',
'pinkal.rathod@inferenz.ai',
'shreya.tiwari@inferenz.ai',
'sumit.thakkar@inferenz.ai',
'akshay.vala@inferenz.ai',
'asjad.puthawala@inferenz.ai',
'ishan.panchal@inferenz.ai',
'hetvi.desai@inferenz.ai',
'piyush.bidwai@inferenz.ai',
'trupti.thakar@inferenz.ai',
'kishan.thakkar@inferenz.ai',
'ashish.sakhare@inferenz.ai',
'sandeep.suthar@inferenz.ai',
'sujeet.pawar@inferenz.ai',
'yash.upadhyaya@inferenz.ai',
'naimish.gohil@inferenz.ai',
'nidhi.thakkar@inferenz.ai',
'ankit.gupta@inferenz.ai',
'bhargav.parmar@inferenz.ai',
'krupa.deria@inferenz.ai',
'prerna.shelke@inferenz.ai',
'simran.ladhani@inferenz.ai',
'rahul.pal@inferenz.ai',
'gaurang.prajapati@inferenz.ai',
'maharshi.shukla@inferenz.ai',
'rajan.hansora@inferenz.ai',
'anurag.bhuingal@inferenz.ai',
'sanny.chauhan@inferenz.ai',
'adarsh.mishra@inferenz.ai',
'sushil.suthar@inferenz.ai',
'vikas.rathod@inferenz.ai',
'ali.panjwani@inferenz.ai',
'akshit.trivedi@inferenz.ai',
'hardik.gohel@inferenz.ai',
'vaishnavi.bharne@inferenz.ai',
'pooja.bagane@inferenz.ai',
'rohit.gaddamidi@inferenz.ai',
'lusy.patel@inferenz.ai',
'mohit.tahiliani@inferenz.ai',
'komal.dhokai@inferenz.ai',
'ruchit.parmar@inferenz.ai',
'pooja.deokate@inferenz.ai',
'pradeep.thippani@inferenz.ai',
'ankit.shah@inferenz.ai',
'ramesh.mokariya@inferenz.ai',
'samir.thakkar@inferenz.ai',
'jagrut.dave@inferenz.ai',
'tarachand.somjani@inferenz.ai',
'sagar.gulghane@inferenz.ai',
'meet.dalwadi@inferenz.ai',
'rohan.lakhani@inferenz.ai',
'naresha.bhat@inferenz.ai',
'sandesh.gosavi@inferenz.ai',
'harshala.kadam@inferenz.ai',
'devrajsinh.jadeja@inferenz.ai',
'jainam.shah@inferenz.ai',
'nutan.jagnade@inferenz.ai',
'kinjal.thakkar@inferenz.ai',
'trushali.ramoliya@inferenz.ai',
'pinkal.panchal@inferenz.ai',
'hardik.kher@inferenz.ai',
'akash.thakker@inferenz.ai',
'jigar.dabhi@inferenz.ai',
'mohit.ingavale@inferenz.ai',
'preeti.sharma@inferenz.ai',
'suresh.bavaliya@inferenz.ai',
'rajat.sapkal@inferenz.ai',
'sanket.jain@inferenz.ai',
'dhaval.vachheta@inferenz.ai',
'ravi.punna@inferenz.ai',
'ashish.mehta@inferenz.ai',
'priyank.panchal@inferenz.ai',
'smit.shah@inferenz.ai',
'sumit.jamnani@inferenz.ai',
'anuj.upadhyay@inferenz.ai',
'meet.hariyani@inferenz.ai',
'ravi.suthar@inferenz.ai',
'hitesh.suthar@inferenz.ai',
'dhruvil.mehta@inferenz.ai',
'mitul.panchal@inferenz.ai',
'tanmay.trivedi@inferenz.ai',
'mirisha.jarecha@inferenz.ai',
'rutvij.dave@inferenz.ai',
'jaydeep.chaudhary@inferenz.ai',
'diya.mistry@inferenz.ai',
'gaurav.mandloi@inferenz.ai',
'honey.joshi@inferenz.ai',
'viraj.shah@inferenz.ai',
'saurav.purohit@inferenz.ai',
'niti.khamker@inferenz.ai',
'moin.saiyed@inferenz.ai',
'digvijaysinh.chauhan@inferenz.ai',
'abhishek.sunil@inferenz.ai',
'hasnain.motagamwala@inferenz.ai',
'jigar.prajapati@inferenz.ai',
'chirag.narang@inferenz.ai',
'shraddha.sejpal@inferenz.ai',
'dax.jain@inferenz.ai',
'vishva.phadke@inferenz.ai',
'prachi.shah@inferenz.ai',
'gayatri.thakkar@inferenz.ai',
'ankita.kanabar@inferenz.ai',
'anmol.shukla@inferenz.ai',
'prashant.sharma@inferenz.ai',
'vismita.jani@inferenz.ai',
'yash.thakkar@inferenz.ai',
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

  document.getElementById('spin').onclick = () => {
    const randomIndex = Math.floor(Math.random() * emails.length);
    document.getElementById('winner').textContent = `Tag: ${emails[randomIndex]}`;
  };
</script>

</body>
</html>

