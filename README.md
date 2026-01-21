# TT-VIEW
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Search & Like Discovery Demo</title>
<style>
  body {
    background: #0f0f0f;
    color: white;
    font-family: Arial;
    padding: 20px;
  }
  input {
    width: 100%;
    padding: 10px;
    border-radius: 8px;
    border: none;
    margin-bottom: 15px;
    font-size: 16px;
  }
  .user {
    background: #1c1c1c;
    padding: 15px;
    border-radius: 10px;
    margin-bottom: 10px;
  }
  .likes {
    color: #00ffd5;
    font-weight: bold;
  }
</style>
</head>
<body>

<h2>🔍 Search Account</h2>
<input type="text" id="search" placeholder="Search username..." onkeyup="searchUser()">

<div id="results"></div>

<script>
  const users = [
    { username: "admin", likes: 10000 },
    { username: "rohit_ai", likes: 5000 },
    { username: "gaming_zone", likes: 2000 },
    { username: "funny_clips", likes: 1000 },
    { username: "study_tips", likes: 500 }
  ];

  function searchUser() {
    const query = document.getElementById("search").value.toLowerCase();
    const results = document.getElementById("results");
    results.innerHTML = "";

    // Sort by likes (popular first)
    const filtered = users
      .filter(u => u.username.includes(query))
      .sort((a, b) => b.likes - a.likes);

    filtered.forEach(user => {
      results.innerHTML += `
        <div class="user">
          <div>👤 @${user.username}</div>
          <div class="likes">❤️ Likes: ${user.likes}</div>
        </div>
      `;
    });
  }

  // Load all users initially
  searchUser();
</script>

</body>
</html>
