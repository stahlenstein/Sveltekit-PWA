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

<div class="login-content">
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
        <input type="submit" class="btn btn-primary" value="Submit" click="doLogin" />
        <p><a href="google.com">Forgot your password?</a></p>
      </form>
    </div>
  </div>
</div>

<style>
  .login-content {
    position: relative;
    width: 100%;
    align-items: center;
    border-radius: 1rem;
    min-height: 1px;
    padding-right: 15px;
    padding-left: 15px;
    display: block;
  }

  .fields {
    margin-left: auto;
    margin-right: auto;
  }

  .form-group input {
    margin-bottom: 10px;
    width: 100%;
    display: block;
    height: calc(2.25rem + 2px);
    padding: 0.375rem 0.75rem;
    font-size: 1rem;
    line-height: 1.5;
    color: #495057;
    background-color: #fff;
    background-clip: padding-box;
    border: 1px solid #ced4da;
    border-radius: 0.25rem;
    transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
  }

  .btn.btn-primary {
    color: #fff;
    background-color: #007bff;
    display: inline-block;
    font-weight: 400;
    text-align: center;
    white-space: nowrap;
    vertical-align: middle;
    user-select: none;
    border: 1px solid transparent;
    padding: 0.375rem 0.75rem;
    font-size: 1rem;
    line-height: 1.5;
    border-radius: 0.25rem;
    transition: color 0.15s ease-in-out, background-color 0.15s ease-in-out,
      border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
    width: 5rem;
  }

  h1 {
    margin-bottom: 1.5rem;
    color: black;
    font-weight: 400;
  }
</style>
