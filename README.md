# Form-html_css_js
<!DOCTYPE html>
<html>
 <head>     
    <meta charset="utf-8"/>
    <meta name="viewport" content="width=device-width,initial-scale=1"/>
    <title> PMP Rentals</title>
    <link href="form.css" rel="stylesheet" type="text/css"/>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" integrity="sha512-9usAa10IRO0HhonpyAIVpjrylPvoDwiPUiKdWk5t3PyolY1cOd4DSE0Ga+ri4AuTroPR5aQvXU9xC6qOPnzFeg==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    <script defer src= form.js> </script>
 </head>
 
 <body>
    <form id="create-account-form">
        <div class ="title">
            <h2>Create Account</h2>
        </div>

        <div class ="input-group ">
        <label for="username">Name</label>
        <input required type="username" id="username" placeholder=" Name" name="username">
        <i class="fa-solid fa-circle-check"></i>
        <i class="fa-solid fa-circle-exclamation"></i>
        <p> Error message</p>
        </div>

        <div class ="input-group">
            <label for="email">Email</label>
            <input required type="email" id="email" placeholder="Email" name="email">
            <i class="fa-solid fa-circle-check"></i>
            <i class="fa-solid fa-circle-exclamation"></i>
            <p> Error message</p>
            </div>
            <div class ="input-group">
                <label for="username">Password</label>
                <input required type="password" id="password" placeholder=" Password" name="password">
                <i class="fa-solid fa-circle-check"></i>
                <i class="fa-solid fa-circle-exclamation"></i>
                <p> Error message</p>
                </div>
                <div class ="input-group">
                    <label for="confirm-password">Confirm Password</label>
                    <input required type="password" id="confirm-password" placeholder=" Password" name="confirm-password">
                    <i class="fa-solid fa-circle-check"></i>
                    <i class="fa-solid fa-circle-exclamation"></i>
                    <p> Error message</p>
                    </div>
                <button type = "submit" id="subbutton"btn>Submit</button>
      </form>
 
</body>
 
</html>

====================================================CSS FILE=====================================
*{
    padding:0;
    margin:0;
    box-sizing: border-box;
}
body{
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100 vh;
    background-color: brown;
}
#create-account-form{
width: 400px;
padding: 20px;
text-transform: uppercase;
background-color: azure;
}
.title{
     margin-bottom: 20px;
}
.input-group{
    margin-bottom: 20px 0;
    position: relative;
}
.input-group label{
    display: inline-block;
    margin-bottom: 5px;
}
.input-group input{
   display: block;
   width: 100%;
   padding: 10px ;
}
.success input{
    border: 3px green solid;
 }

 .error input{
    border: 3px red solid;
 }
 .error i.fa-circle-exclamation{
    visibility:visible;
    color: red;
}
.input-group i{
    position:absolute;
   right:10px;
   top:35px;
   visibility: hidden;
 }
 .success i.fa-circle-check{
     visibility:visible;
     color: green;
 }
 .input-group p{
    font-size: 15px;
    color: red;
    visibility: hidden;
 }

 .error p{
    visibility:visible;
    
}
 .btn{
     width:100%;
     padding: 10px; 
     font-size: 20;
     background-color: chocolate;
     color: white;
     text-transform: uppercase;
     border:none;
 
    }
    input:invalid{
        background-color:rgb(215, 159, 159);
    }   
    ===========================================================================JS FILE=====================================================
    const form = document.querySelector('#create-account-form');
const emailInput = document.querySelector('#email')
const usernameInput = document.querySelector('#username');
const passwordInput = document.querySelector('#password');
const confirmPasswordInput= document.querySelector('#confirm-password');

let sButton= document.getElementById("subbutton");
sButton.addEventListener("click",validateEmail);
sButton.addEventListener("click",validateName);
sButton.addEventListener("click",validatePass);
sButton.addEventListener("click",validateConfirmPass);
form.addEventListener('submit', (event) =>{
event.preventDefault;

})

 function validateName() {
  let userName = document.getElementById("username");
  
  if (usernameInput.validity.valueMissing){
userName.setCustomValidity("Please enter your name before you submit")
  }
 else{
   userName.setCustomValidity("")
 }  
}

function validateEmail() {
  let emailInpt = document.getElementById("email")
  let validEmail = /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/;

  if (emailInpt.value.match(validEmail)) {
    emailInput.setCustomValidity("")
   
    email.focus();

  } else {

    emailInpt.setCustomValidity("Your email is invalid. You should follow email conventions");

  }

}
function validatePass() {
  let passInput = document.getElementById("password");
  let decimal=  /^(?=.*\d)(?=.*[a-z])(?=.*[A-Z])(?=.*[^a-zA-Z0-9])(?!.*\s).{8,15}$/;

  if (passInput.value.match(decimal)) {
    passInput.setCustomValidity("")

  } else {

    passInput.setCustomValidity("Password must be 8 to 15 characters which contain at least one lowercase letter, one uppercase letter, one numeric digit, and one special character");

  }

}
function validateConfirmPass() {
  let passInput = document.getElementById("password").value;
  let confirmpassInput = document.getElementById("confirm-password").value;
  let passInput2 = document.getElementById("password");
  let confirmpassInput2 = document.getElementById("confirm-password");
  if (passInput!= confirmpassInput) {
   
 confirmpassInput2.setCustomValidity("Make sure both passwords are look the same");

  } else {
 confirmpassInput2.setCustomValidity("")
    }

}
