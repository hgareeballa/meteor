<script>
  import { Meteor } from "meteor/meteor";

  let username = "";
  let password = "";
  let message = "";

  const handleSubmit = () => {
    console.log("Login...!");
    message = "";
    Meteor.loginWithPassword(username, password, function (err) {  
      if (err) {
        message = "Invalid User/Pass !";
      }else{
        message = "success";
      }
    });
  };
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
    <button type="submit">Log In</button>
  </div>
  <div>
    {message}
  </div>
</form>

