<script>
  import { Meteor } from "meteor/meteor";

  let username = "";
  let password = "";
  let message = "";

  const handleSubmit = () => {
    console.log("Login...!");
    message = "...";
    Meteor.loginWithPassword(username, password, function (err) {  
    message = "success";
      if (err) {
        message = "Invalid User/Pass !";
      }
    });
  };

  const handleRegister = () => {
    console.log("Register...!");
    message = "...";

    Accounts.createUser({
      username: username,
      password: password,
    }, function (err){
        if (err){
            alert(err);
        }else{
          alert('User Registered Successfully!');
        }
    });
  }
</script>

<form class="login-form" on:submit|preventDefault={handleSubmit}>
  
  <div>
    <label htmlFor="username">Username</label>
    <input
      type="text"
      placeholder="Username"
      name="username"
      required
      bind:value={username}
    />
  </div>

  <div>
    <label htmlFor="password">Password</label>
    <input
      type="password"
      placeholder="Password"
      name="password"
      required
      bind:value={password}
    />
  </div>
  <div>
    <button type="submit">Log In</button>  <button type="Button" on:click={handleRegister}>Register</button> 
  </div>
  <div>
    {message}
  </div>
</form>

