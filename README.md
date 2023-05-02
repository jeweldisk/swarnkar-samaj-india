# swarnkar-samaj-india
Swarnkar Samaj India App is For Only Swarnkar Samaj People
<!DOCTYPE html>
<html>
<head>
	<title>Join Us Form</title>
	<style>
    body {
	font-family: Arial, sans-serif;
	margin: 0;
	padding: 0;
}

header {
	background-color: #f2f2f2;
	padding: 20px;
	text-align: center;
}

h1 {
	text-align: center;
	padding: 50px 0;
}

form {
	width: 600px;
	margin: 0 auto;
}

label {
	display: block;
	margin-bottom: 10px;
	font-size: 18px;
}

input[type="text"],
input[type="email"],
input[type="tel"],
select {
	width: 100%;
	padding: 10px;
	font-size: 16px;
	border: 1px solid #ccc;
	border-radius: 5px;
	margin-bottom: 20px;
}

button {
	background-color: #4CAF50;
	color: white;
	padding: 10px 20px;
	border: none;
	border-radius: 5px;
	cursor: pointer;
}

button:hover {
	background-color: #3e8e41;
}


    </Style>
</head>
<body>
	<header>
		<img src="logo.png" alt="Swarnkar Samaj India App">
	</header>

	<h1>Join Swarnkar Samaj India App</h1>

	<form>
		<label for="name">स्वर्णकार बंधु का नाम</label>
		<input type="text" id="name" name="name" required>

		<label for="gotra">गोत्र का नाम:</label>
		<input type="text" id="gotra" name="gotra" required>

		<label for="sub-caste">Sub Caste:</label>
		<select id="samaj" name="samaj">
    <option
  value="ब्राह्मणीय">ब्राह्मणीय</option>    <option
     value="श्रीमाली">श्रीमाली</option>        <option                             value="मैढ़क्षत्रिय">मैढ़क्षत्रिय</option>    </option>
      </select>

		<label for="designation">समाज में आपका पद :</label>
		<select id="samaj" name="samaj">
    <option
  value="Chairman">Chairman</option>    <option
     value="Member">Member</option>        <option                             value="Sachiv">Sachiv</option>    </option>
      </select>

		<label for="samaj">आपके समाज की कार्यकारिणी का नाम</label>
		<select id="samaj" name="samaj">
			<option value="Ahmedabad">Ahmedabad</option>
			<option value="Mumbai">Mumbai</option>
			<option value="Delhi">Delhi</option>
			<option value="Jaipur">Jaipur</option>
			<option value="Surat">Surat</option>
		</select>

		<label for="mobile-number">Mobile Number:</label>
		<input type="tel" id="mobile-number" name="mobile-number" pattern="[0-9]{10}" required>

		<label for="whatsapp-number">WhatsApp Number:</label>
		<input type="tel" id="whatsapp-number" name="whatsapp-number" pattern="[0-9]{10}" required>

		<label for="email">Email Address:</label>
		<input type="email" id="email" name="email" required>

		<label for="profession">Profession/ Jewellers Name:</label>
		<input type="text" id="profession" name="profession" required>

		<label for="pincode">Pincode:</label>
		<input type="text" id="pincode" name="pincode" pattern="[0-9]{6}" required>

		<button type="submit" id="submit-btn">Submit</button>
	</form>

	<script>
    const form = document.querySelector('form');
const nameInput = document.querySelector('#name');
const gotraInput = document.querySelector('#gotra');
const subCasteInput = document.querySelector('#sub-caste');
const designationInput = document.querySelector('#designation');
const samajSelect = document.querySelector('#samaj');
const mobileNumberInput = document.querySelector('#mobile-number');
const whatsappNumberInput = document.querySelector('#whatsapp-number');
const emailInput = document.querySelector('#email');
const professionInput = document.querySelector('#profession');
const pincodeInput = document.querySelector('#pincode');
const submitBtn = document.querySelector('#submit-btn');

form.addEventListener('submit', function(event) {
	event.preventDefault();

	// Validate inputs
	if (nameInput.value === '') {
		showError(nameInput, 'Name is required');
	} else {
		hideError(nameInput);
	}

	if (gotraInput.value === '') {
		showError(gotraInput, 'Gotra is required');
	} else {
		hideError(gotraInput);
	}

	if (subCasteInput.value === '') {
		showError(subCasteInput, 'Sub Caste is required');
	} else {
		hideError(subCasteInput);
	}

	if (designationInput.value === '') {
		showError(designationInput, 'Designation is required');
	} else {
		hideError(designationInput);
	}

	if (samajSelect.value === '') {
		showError(samajSelect, 'Samaj is required');
	} else {
		hideError(samajSelect);
	}

	if (mobileNumberInput.value === '') {
		showError(mobileNumberInput, 'Mobile Number is required');
	} else if (!isValidMobileNumber(mobileNumberInput.value)) {
		showError(mobileNumberInput, 'Mobile Number is invalid');
	} else {
		hideError(mobileNumberInput);
	}

	if (whatsappNumberInput.value === '') {
		showError(whatsappNumberInput, 'WhatsApp Number is required');
	} else if (!isValidMobileNumber(whatsappNumberInput.value)) {
		showError(whatsappNumberInput, 'WhatsApp Number is invalid');
	} else {
		hideError(whatsappNumberInput);
	}

	if (emailInput.value === '') {
		showError(emailInput, 'Email Address is required');
	} else if (!isValidEmail(emailInput.value)) {
		showError(emailInput, 'Email Address is invalid');
	} else {
		hideError(emailInput);
	}

	if (professionInput.value === '') {
		showError(professionInput, 'Profession/Jewellers Name is required');
	} else {
		hideError(professionInput);
	}

	if (pincodeInput.value === '') {
		showError(pincodeInput, 'Pincode is required');
	} else if (!isValidPincode(pincodeInput.value)) {
		showError(pincodeInput, 'Pincode is invalid');
	} else {
		hideError(pincodeInput);
	}

	// Submit form if all inputs are valid
	if (!document.querySelectorAll('.error').length) {
		form.submit();
	}
});

function showError(input, message) {
	const error = document.createElement('div');
	error.classList.add('error');
	error.innerText = message;
	input.parentElement.insertBefore(error, input.nextElementSibling);
}

function hideError(input) {
	const error = input.parentElement.querySelector('.error');
	if (error) {
		error.remove();
	}
}

function isValidEmail(email) {
	const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
	return regex.test(email);
}

function isValidMobileNumber(number) {
	const regex = /^[0-9]{10

  </script>
</body>
</html>
