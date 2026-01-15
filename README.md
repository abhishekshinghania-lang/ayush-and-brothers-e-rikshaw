<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ayush and Brothers E-Rickshaw Booking</title>
  <style>
    body { margin:0; font-family:Arial, Helvetica, sans-serif; background:#f4f6f8; color:#333; }
    header { background:#0a7cff; color:#fff; padding:20px; text-align:center; }
    header h1 { margin:0; font-size:28px; }
    header p { margin:5px 0; }
    .lang-toggle { position:absolute; top:20px; right:20px; }
    .lang-toggle button { margin-left:5px; padding:5px 10px; cursor:pointer; }
    .container { max-width:1100px; margin:auto; padding:20px; }
    .hero { display:grid; grid-template-columns:1fr 1fr; gap:20px; align-items:center; }
    .hero img { width:100%; border-radius:12px; }
    .card { background:#fff; padding:20px; border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.08); margin-top:30px; }
    form { display:grid; grid-template-columns:1fr 1fr; gap:15px; }
    form input, form select, form textarea { padding:10px; border-radius:6px; border:1px solid #ccc; }
    textarea, .full { grid-column:span 2; }
    button { background:#0a7cff; color:#fff; padding:12px; border:none; border-radius:8px; cursor:pointer; }
    button:hover { background:#055fd1; }
    .features { display:grid; grid-template-columns:repeat(auto-fit, minmax(220px,1fr)); gap:20px; margin-top:30px; }
    .feature-box { background:#fff; padding:20px; border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.08); text-align:center; }
    table { width:100%; border-collapse:collapse; }
    table, th, td { border:1px solid #ccc; }
    th, td { padding:8px; text-align:left; }
    footer { background:#222; color:#fff; text-align:center; padding:15px; margin-top:40px; }
    @media(max-width:768px){ .hero{grid-template-columns:1fr;} form{grid-template-columns:1fr;} textarea,.full{grid-column:span 1;} }
  </style>
</head>
<body>
<header>
  <h1 id="title">Ayush and Brothers E-Rickshaw Booking</h1>
  <p id="subtitle">Safe • Affordable • Easy Booking</p>
  <p>Company: Ayush and Brothers | Contact: 9431239445, 9122143666</p>
  <p>Address: Bairiya Paigemberpur, near Bairiya Bus Stand, in front of Bank of India, Ayachigram, Muzaffarpur, Bihar 842003</p>
  <div class="lang-toggle">
    <button onclick="setLang('en')">EN</button>
    <button onclick="setLang('hi')">हिंदी</button>
  </div>
</header>

<div class="container">
  <section class="hero">
    <div>
      <h2 id="heroTitle">Buy or Book E-Rickshaw from Home</h2>
      <p id="heroText">Choose your preferred model, pay small booking amount, and our team will contact you for delivery.</p>
    </div>
    <img src="https://images.unsplash.com/photo-1606391901318-07003db08d44" />
  </section>

  <section class="card">
    <h3 id="formTitle">Customer Booking Form</h3>
    <form id="bookingForm">
      <input id="name" placeholder="Full Name" required />
      <input id="mobile" placeholder="Mobile Number" required />
      <input id="city" placeholder="City" required />
      <select id="model" required>
        <option value="">Select E-Rickshaw Model</option>
        <option value="Passenger">Passenger E-Rickshaw – ₹1,50,000</option>
        <option value="Loader">Loader E-Rickshaw – ₹1,70,000</option>
        <option value="Cart">Electric Cart – ₹1,30,000</option>
      </select>
      <select id="type" required>
        <option value="">Booking Type</option>
        <option>Purchase</option>
        <option>Test Drive</option>
      </select>
      <textarea id="note" placeholder="Any special requirement or question"></textarea>
      <button class="full" type="submit">Pay ₹1,000 & Book (UPI)</button>
    </form>
  </section>

  <section class="card">
    <h3>Admin Panel (Demo)</h3>
    <table id="adminTable">
      <tr><th>Name</th><th>Mobile</th><th>City</th><th>Model</th></tr>
    </table>
  </section>

  <section class="features">
    <div class="feature-box"><h4>Online Booking</h4><p>Book from home</p></div>
    <div class="feature-box"><h4>WhatsApp Confirmation</h4><p>Instant message to customer and owner</p></div>
    <div class="feature-box"><h4>Secure Payment</h4><p>Booking amount only</p></div>
  </section>
</div>

<footer>
  <p>© 2026 Ayush and Brothers</p>
</footer>

<script>
  const bookings = [];
  document.getElementById('bookingForm').addEventListener('submit', function(e){
    e.preventDefault();
    const name = nameEl.value;
    const mobile = mobileEl.value;
    const city = cityEl.value;
    const model = modelEl.value;
    bookings.push({name,mobile,city,model});
    const row = adminTable.insertRow();
    row.insertCell(0).innerText=name;
    row.insertCell(1).innerText=mobile;
    row.insertCell(2).innerText=city;
    row.insertCell(3).innerText=model;
    // Customer WhatsApp
    window.open(`https://wa.me/91${mobile}?text=Thank you ${name}, your e-rickshaw booking for ${model} is received.`);
    // Owner WhatsApp
    window.open(`https://wa.me/919431239445?text=New E-Rickshaw Booking%0AName:${name}%0AMobile:${mobile}%0ACity:${city}%0AModel:${model}`);
    window.open(`https://wa.me/919122143666?text=New E-Rickshaw Booking%0AName:${name}%0AMobile:${mobile}%0ACity:${city}%0AModel:${model}`);
    alert('Booking request submitted. Payment integration required.');
    this.reset();
  });
  const nameEl=name, mobileEl=mobile, cityEl=city, modelEl=model;
  function setLang(l){
    if(l==='hi'){
      title.innerText='आयुष एंड ब्रदर्स ई-रिक्शा ऑनलाइन बुकिंग';
      subtitle.innerText='सुरक्षित • सस्ता • आसान बुकिंग';
      heroTitle.innerText='घर बैठे ई-रिक्शा खरीदें या बुक करें';
      heroText.innerText='मॉडल चुनें, ऑनलाइन बुक करें और हम डिलीवरी संभालेंगे';
      formTitle.innerText='ग्राहक बुकिंग फॉर्म';
    } else location.reload();
  }
</script>
</body>
</html>
