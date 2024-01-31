<script>
  import logo from '$lib/assets/logo.png';
</script>

<h1>Lock the Loo</h1>
<img src={logo} alt="Lock the Loo logo is of a smiling door giving thumbs up" />
<p>
  When visiting a public toilet, we need to make sure the door is locked. Get all the training needed to be a responsible and aware employee
  in a workplace environment.
</p>

<a href="/game">Get started</a>

<style>
  p {
    margin-top: 20px;
    margin-bottom: 20px;
    max-width: 60ch;
  }

  img {
    max-width: min(400px, 100%);
    width: auto;
    height: auto;
  }

  a {
    display: inline-block;
    padding: 10px 20px;
    text-align: center;
    text-decoration: none;
    color: white;
    background-color: #007bff;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
    transition:
      background-color 0.3s,
      box-shadow 0.3s;
  }

  a:hover {
    background-color: #0056b3;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  }

  a:active {
    background-color: #004085;
    box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.3);
  }
</style>
