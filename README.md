/*
Create a file server.js and run: node server.js


This server exposes two endpoints:
POST /api/create-order -> creates Razorpay order and returns order details to client
POST /api/verify-payment -> verifies signature after payment


Don't forget to set RAZORPAY_KEY_ID and RAZORPAY_KEY_SECRET in your env.
*/


/* server.js */


// const express = require('express');
// const Razorpay = require('razorpay');
// const bodyParser = require('body-parser');
// const crypto = require('crypto');
// const cors = require('cors');


// const app = express();
// app.use(bodyParser.json());
// app.use(cors());


// const razorpay = new Razorpay({
// key_id: process.env.RAZORPAY_KEY_ID || 'rzp_test_YOUR_KEY',
// key_secret: process.env.RAZORPAY_KEY_SECRET || 'rzp_test_YOUR_SECRET'
// });


// // Create order
// app.post('/api/create-order', async (req, res) => {
// try {
// const { amount, productId } = req.body;
// // You can create an order in Razorpay with amount (in paise) and currency
// const options = {
// amount: amount, // amount in the smallest currency unit (eg. paise)
// currency: 'INR',
// receipt: `receipt_order_${Date.now()}`
// };
// const order = await razorpay.orders.create(options);
// return res.json(order);
// } catch (err) {
// console.error(err);
// res.status(500).json({ error: 'order creation failed' });
// }
// });


// // Verify payment
// app.post('/api/verify-payment', (req, res) => {
// const { razorpay_payment_id, razorpay_order_id, razorpay_signature } = req.body;
// const body = razorpay_order_id + '|' + razorpay_payment_id;
// const expectedSignature = crypto.createHmac('sha256', process.env.RAZORPAY_KEY_SECRET || 'rzp_test_YOUR_SECRET')
// .update(body.toString())
// .digest('hex');
// const isValid = expectedSignature === razorpay_signature;
// if (isValid) {
// // save order in DB, mark as paid
// return res.json({ valid: true });
// } else {
// return res.json({ valid: false });
// }
// });


// app.listen(4000, () => console.log('Server running on port 4000'));


/* --------------------
Instructions / Notes
--------------------
1) Add the Razorpay checkout script to `public/index.html`:
<script src="https://checkout.razorpay.com/v1/checkout.js"></script>


2) Use environment variables for keys. In React, set REACT_APP_RAZORPAY_KEY for client key.
Example .env.development:
REACT_APP_RAZORPAY_KEY=rzp_test_YOUR_KEY


3) Always create orders on server using your KEY_SECRET — never from frontend.


4) After payment, verify the signature on server using HMAC SHA256 as shown.


5) For production, replace test keys with live keys and enable HTTPS.


6) Optionally, integrate email/SMS notifications and store order details in DB.


*/
