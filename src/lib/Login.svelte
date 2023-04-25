<script>
  import user from "../user";
  let username = "";
  let password = "";
  let currentError = null;

  const login = () => {
    fetch("url", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({ username: username, password: password }),
    })
      .then((res) => {
        if (res.status < 299) return res.json();
        if (res.status > 299) currentError = "Server Error";
      })
      .then((data) => {
        if (data) user.update((val) => (val = { ...data }));
      })
      .catch((error) => {
        currentError = error;
        console.log("Error logging in: ", error);
      });
  };
</script>

<div class="login-page">
    <div class="row">
      <div class="fields">
        <h1>Sign In</h1>
        <form on:submit|preventDefault={login} class="form-group">
          <input
            bind:value={username}
            id="username"
            type="email"
            class="form-control"
            placeholder="Email"
            required
          />
          <input
            bind:value={password}
            id="password"
            type="password"
            class="form-control"
            placeholder="Password"
            required
          />
          <input type="submit" class="btn btn-primary" click="doLogin" />
          <p><a href="#">Forgot your password?</a></p>
        </form>
      </div>
    </div>
</div>

<style>
  .login-page {
    align-items: center;
    display: flex;
    height: 100vh;
  }

  .fields {
    margin-left: auto;
    margin-right: auto;
  }

  .form-group input {
    margin-bottom: 20px;
  }
</style>
