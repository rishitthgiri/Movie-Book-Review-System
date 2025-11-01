<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ReviewHub - Movies & Books</title>
<style>
/* --- CSS: Same beautiful visuals and stable buttons as previous --- */
body {
  font-family: 'Montserrat', Arial, sans-serif;
  margin: 0;
  padding: 0;
  min-height: 100vh;
  background: url("https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=1500&q=80") center/cover no-repeat fixed, 
              linear-gradient(135deg,#5EFCE8 0%, #736EFE 100%);
  position: relative;
}
body:before {
  content: "";
  position: fixed;
  z-index: -1;
  top:0; left:0; bottom:0; right:0;
  background: linear-gradient(120deg, rgba(60,60,120,0.30) 30%, rgba(55,240,230,0.16) 70%);
  mix-blend-mode: multiply;
  pointer-events: none;
}
header {
  background: rgba(40,40,70,0.88);
  color: #fff;
  padding: 2rem 1.5rem 1.2rem 1.5rem;
  text-align: left;
  box-shadow: 0 4px 20px rgba(70,50,140,0.15);
  border-bottom-left-radius: 25px;
  border-bottom-right-radius: 25px;
  letter-spacing: 1px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
h1 {
  font-family: 'Poppins', Arial, sans-serif;
  font-size: 2.7rem;
  margin: 0;
  letter-spacing: 4px;
  font-weight: 700;
  background: linear-gradient(to right,#5EFCE8,#736EFE);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
#auth-controls {
  display: flex;
  align-items: center;
  gap: 1rem;
  font-size:1.11rem;
  color: #EFEFF7;
  font-weight:600;
}
#user-info { margin-right:0.2rem; }
nav {
  background: transparent;
  padding: 1rem 0 0.9rem 0;
  display: flex;
  justify-content: center;
  gap: 0.6rem;
  position: relative;
  z-index: 100;
}
nav a {
  background: rgba(255,255,255,0.21);
  color: #4345a7;
  font-size: 1.14rem;
  padding: 0.7rem 1.8rem;
  border-radius: 20px;
  text-decoration: none;
  font-family: 'Montserrat', Arial, sans-serif;
  margin: 0 0.1rem;
  transition: background 0.3s, color 0.2s, box-shadow 0.3s, transform 0.17s;
  box-shadow: 0 2px 10px rgba(40,40,70,0.07);
}
nav a:hover, nav a:focus {
  background: linear-gradient(90deg, #736EFE 10%, #5EFCE8 90%);
  color: #fff;
  transform: scale(1.07) translateY(-1.5px);
  box-shadow: 0 4px 18px rgba(75,60,180,0.18);
}
main {
  padding: 1.5rem;
  max-width: 1200px;
  margin: auto;
}
section {
  margin-bottom: 2.5rem;
  padding: 1.5rem 1rem;
  border-radius: 20px;
  background: rgba(255,255,255,0.45);
  box-shadow: 0 8px 28px rgba(0,0,70,0.16);
  backdrop-filter: blur(15px);
  border: 1.2px solid #736EFE40;
  overflow:visible;
}
h2 {
  font-size: 1.6rem;
  padding-bottom: 0.3rem;
  color: #4345a7;
  border-bottom: 2px solid #736EFE;
}
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1.4rem;
  justify-content: flex-start;
}
.card {
  background: rgba(255,255,255,0.8);
  border-radius: 20px;
  box-shadow: 0 10px 32px rgba(85,70,200,0.13);
  width: 185px;
  cursor: pointer;
  transition: transform 0.2s, box-shadow 0.27s, background 0.3s;
  overflow: hidden;
  border: 1px solid #dff3fe;
  backdrop-filter: blur(8px);
  position: relative;
}
.card:hover, .card:focus {
  transform: scale(1.055) translateY(-2px);
  box-shadow: 0 22px 34px rgba(80,60,200,0.18);
  background: linear-gradient(135deg,#dff3fe 40%, #eceafd 100%);
}
.card img {
  width: 100%;
  height: 255px;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  object-fit: cover;
  box-shadow: 0 6px 14px rgba(60,80,150,0.13);
  background: #dae8ff;
}
.card .info {
  padding: 0.7rem 0.9rem;
}
.card .info h3 {
  margin: 0.3rem 0 0.12rem 0;
  font-size: 1.05rem;
  color: #31255d;
  font-weight: 600;
  letter-spacing: 0.8px;
}
.card .info p {
  margin: 0.15rem 0;
  font-size: 0.96rem;
  color: #515287;
}
.rating-span {
  color: #736EFE;
  font-weight: 700;
  font-size: 1.10rem;
  letter-spacing: 1px;
}
button {
  padding: 0.63rem 1.3rem;
  border: none;
  border-radius: 15px;
  background: linear-gradient(90deg,#5EFCE8,#736EFE);
  color: #fff;
  cursor: pointer;
  font-weight: 600;
  font-size: 1.11rem;
  font-family: 'Montserrat', Arial, sans-serif;
  transition: box-shadow 0.27s, background 0.34s;
  box-shadow: 0 2px 16px rgba(85,70,200,0.14);
  margin-top: 0.6rem;
}
button:hover, button:focus {
  background: linear-gradient(90deg,#736EFE,#5EFCE8 80%);
  box-shadow: 0 6px 26px rgba(60,60,160,0.19);
}
form {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  max-width: 330px;
  margin-bottom: 1.5rem;
}
input, select, textarea {
  padding: 0.58rem;
  border-radius: 12px;
  border: 1px solid #8ec9d6;
  font-size: 1.06rem;
  background: rgba(255,255,255,0.7);
  box-shadow: 0 1px 6px rgba(80,60,130,0.04);
  transition: border 0.2s;
}
input:focus, select:focus, textarea:focus {
  border: 1.7px solid #736EFE;
  outline: none;
}
textarea {
  resize: vertical;
  min-height: 70px;
}
table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 1rem;
  background: rgba(255,255,255,0.65);
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 6px 22px rgba(66,66,160,0.07);
}
th, td {
  padding: 0.7rem;
  border: 1px solid #dbdbfd;
  text-align: left;
  font-size: 1rem;
}
th {
  background: linear-gradient(90deg,#736EFE,#5EFCE8);
  color: white;
  font-weight: 600;
}
tr:nth-child(even) td {
  background: #eef7fa;
}
.spinner {
  border: 8px solid #f3f3f3;
  border-top: 8px solid #736EFE;
  border-radius: 50%;
  width:50px;
  height:50px;
  animation:spin 1s linear infinite;
  margin: 2rem auto;
  display: block;
}
@keyframes spin {100% {transform: rotate(360deg);}
}
[tabindex="0"]:focus {outline: 3px solid #736EFE;}
#login-modal form {
  background: rgba(255,255,255,0.85);
  border-radius: 22px;
  box-shadow: 0 9px 32px rgba(85,70,160,0.15);
  border: 1px solid #a3cffc;
  padding: 2.1rem 2.3rem;
  min-width: 260px;
}
#login-modal {
  display: none;
  position: fixed;
  top:0; left:0; width:100vw; height:100vh;
  background: rgba(53, 61, 114, 0.29);
  z-index:1000; align-items:center; justify-content: center;
  transition: background 0.3s;
}
@media(max-width: 900px) {
  main {padding:0.5rem;}
  .card-container {gap:1rem;}
  section {padding:0.8rem 0.5rem;}
  header {padding: 1.1rem;}
  h1 {font-size:2.2rem;}
  #auth-controls {position:static;}
}
@media(max-width: 600px) {
  .card-container {flex-direction: column; align-items: center;}
  nav {flex-direction: column;}
  nav a {width: 100%; text-align: left; border-bottom: 1px solid #222;}
  header {font-size: 0.85rem; flex-direction: column; align-items: flex-start;}
  h1 {font-size:1.7rem;}
  #auth-controls {margin-top:0.6rem;}
  main {padding:0.3rem;}
}
h3, h4 {
  color: #736EFE;
  margin-top: 1rem;
  margin-bottom: 0.4rem;
}
a {
  color: #736EFE;
  text-decoration: underline;
}
a:hover {
  color: #4345a7;
}
::-webkit-scrollbar {
  width: 9px;
  background: #eceafd;
}
::-webkit-scrollbar-thumb {
  background: linear-gradient(90deg,#5EFCE8,#736EFE);
  border-radius: 9px;
}
</style>
</head>
<body>
<header>
  <h1>ReviewHub</h1>
  <div id="auth-controls">
    <span id="user-info"></span>
    <button id="login-btn" onclick="showLoginModal()" aria-label="Login">Login</button>
    <button id="logout-btn" onclick="logoutUser()" aria-label="Logout" style="display:none;">Logout</button>
  </div>
</header>
<nav role="navigation" aria-label="Site navigation">
  <a href="#home" tabindex="0">Home</a>
  <a href="#movies" tabindex="0">Movies</a>
  <a href="#books" tabindex="0">Books</a>
  <a href="#reviews" tabindex="0">Reviews</a>
  <a href="#admin" tabindex="0">Admin</a>
</nav>
<main id="main-content" aria-live="polite"></main>
<div id="login-modal">
  <form id="login-form" onsubmit="login(event)">
    <h3>Login/Register</h3>
    <label>Username:</label>
    <input aria-label="Username" name="username" required>
    <label>Password:</label>
    <input aria-label="Password" type="password" name="password" required>
    <button type="submit">Submit</button>
    <button type="button" onclick="hideLoginModal()">Cancel</button>
    <div id="login-error" style="color:red;margin-top:0.5rem;"></div>
  </form>
</div>
<script>
let movies = [
  {id:1, title:"The Shawshank Redemption", genre:"Drama", rating:9.3, img:"https://image.tmdb.org/t/p/w500/9O7gLzmreU0nGkIB6K3BsJbzvNv.jpg"},
  {id:2, title:"The Godfather", genre:"Crime", rating:9.2, img:"https://image.tmdb.org/t/p/w500/3bhkrj58Vtu7enYsRolD1fZdja1.jpg"},
  {id:3, title:"The Dark Knight", genre:"Action", rating:9.0, img:"https://image.tmdb.org/t/p/w500/qJ2tW6WMUDux911r6m7haRef0WH.jpg"},
  {id:4, title:"12 Angry Men", genre:"Drama", rating:9.0, img:"https://image.tmdb.org/t/p/w500/ppd84D0iBdfPQ6sFw0i2pbqBjLL.jpg"},
  {id:5, title:"Schindler's List", genre:"Biography", rating:8.9, img:"https://image.tmdb.org/t/p/w500/sF1U4EUQS8YHUYjNl3pS2F9JTri.jpg"},
  {id:6, title:"Pulp Fiction", genre:"Crime", rating:8.9, img:"https://image.tmdb.org/t/p/w500/d5iIlFn5s0ImszYzBPb8JPIfbXD.jpg"},
  {id:7, title:"The Lord of the Rings: The Return of the King", genre:"Fantasy", rating:8.9, img:"https://image.tmdb.org/t/p/w500/rCzpDGLbOoPwLjy3OAm5NUPOTrC.jpg"},
  {id:8, title:"Forrest Gump", genre:"Drama", rating:8.8, img:"https://image.tmdb.org/t/p/w500/h5J4W4veyxMXDMjeNxC9M0l5Ko7.jpg"},
  {id:9, title:"Inception", genre:"Sci-Fi", rating:8.7, img:"https://image.tmdb.org/t/p/w500/9gk7adHYeDvHkCSEqAvQNLV5Uge.jpg"},
  {id:10, title:"Fight Club", genre:"Drama", rating:8.8, img:"https://image.tmdb.org/t/p/w500/pB8BM7pdSp6B6Ih7QZ4DrQ3BmJK.jpg"},
  {id:11, title:"The Matrix", genre:"Sci-Fi", rating:8.7, img:"https://image.tmdb.org/t/p/w500/f89U3ADr1oiB1s9GkdPOEpXUk5d.jpg"},
  {id:12, title:"Goodfellas", genre:"Crime", rating:8.7, img:"https://image.tmdb.org/t/p/w500/aKuFiU82sOxBtUtUy3kT8O0hS3N.jpg"},
  {id:13, title:"Se7en", genre:"Crime", rating:8.6, img:"https://image.tmdb.org/t/p/w500/6yoghtyTpznpBAs6jR3zvY2B1Y7.jpg"},
  {id:14, title:"Interstellar", genre:"Sci-Fi", rating:8.6, img:"https://image.tmdb.org/t/p/w500/gEU2QniE6E77NI6lCU6MxlNBvIx.jpg"},
  {id:15, title:"The Green Mile", genre:"Drama", rating:8.6, img:"https://image.tmdb.org/t/p/w500/velWPhVMQeQBiE19Zc0WOs0aN2.jpg"},
  {id:16, title:"Parasite", genre:"Thriller", rating:8.6, img:"https://image.tmdb.org/t/p/w500/7IiTTgloJzvGI1TAYymCfbfl3vT.jpg"},
  {id:17, title:"The Lion King", genre:"Animation", rating:8.5, img:"https://image.tmdb.org/t/p/w500/2DtP6CkACM9iJByUwtTqvpQfbeF.jpg"},
  {id:18, title:"Gladiator", genre:"Action", rating:8.5, img:"https://image.tmdb.org/t/p/w500/ty8FEOHLMxZznBqT14QjteGFT6E.jpg"},
  {id:19, title:"Saving Private Ryan", genre:"War", rating:8.6, img:"https://image.tmdb.org/t/p/w500/1wY4psJ5Kmmg9gN3k4Z6r3j1Lgd.jpg"},
  {id:20, title:"Whiplash", genre:"Drama", rating:8.5, img:"https://image.tmdb.org/t/p/w500/oPxnRhyAIzJKGUEdSiwTJQBa6zV.jpg"}
];
let books = [
  {id:1, title:"To Kill a Mockingbird", genre:"Fiction", rating:9.3, img:"https://images-na.ssl-images-amazon.com/images/I/81aY1lxk+EL._AC_UL320_SR320,320_.jpg"},
  {id:2, title:"1984", genre:"Dystopian", rating:9.0, img:"https://images-na.ssl-images-amazon.com/images/I/71kxa1-0mfL._AC_UL320_SR320,320_.jpg"},
  {id:3, title:"The Great Gatsby", genre:"Fiction", rating:8.8, img:"https://images-na.ssl-images-amazon.com/images/I/81af+MCATTL._AC_UL320_SR320,320_.jpg"},
  {id:4, title:"The Catcher in the Rye", genre:"Fiction", rating:8.5, img:"https://images-na.ssl-images-amazon.com/images/I/91HPG31dTwL._AC_UL320_SR320,320_.jpg"},
  {id:5, title:"The Hobbit", genre:"Fantasy", rating:9.0, img:"https://images-na.ssl-images-amazon.com/images/I/91b0C2YNSrL._AC_UL320_SR320,320_.jpg"},
  {id:6, title:"Fahrenheit 451", genre:"Dystopian", rating:8.7, img:"https://images-na.ssl-images-amazon.com/images/I/71OFqSRFDgL._AC_UL320_SR320,320_.jpg"},
  {id:7, title:"Jane Eyre", genre:"Romance", rating:8.9, img:"https://images-na.ssl-images-amazon.com/images/I/81xVrs6n6YL._AC_UL320_SR320,320_.jpg"},
  {id:8, title:"Pride and Prejudice", genre:"Romance", rating:9.1, img:"https://images-na.ssl-images-amazon.com/images/I/81NCSxb2g1L._AC_UL320_SR320,320_.jpg"},
  {id:9, title:"The Lord of the Rings", genre:"Fantasy", rating:9.2, img:"https://images-na.ssl-images-amazon.com/images/I/91Ur3R5pKML._AC_UL320_SR320,320_.jpg"},
  {id:10, title:"Animal Farm", genre:"Dystopian", rating:8.8, img:"https://images-na.ssl-images-amazon.com/images/I/91LUbA5Dz6L._AC_UL320_SR320,320_.jpg"},
  {id:11, title:"Moby Dick", genre:"Adventure", rating:8.4, img:"https://images-na.ssl-images-amazon.com/images/I/81A6+ozm3PL._AC_UL320_SR320,320_.jpg"},
  {id:12, title:"War and Peace", genre:"Historical", rating:9.0, img:"https://images-na.ssl-images-amazon.com/images/I/91HHqVTAJQL._AC_UL320_SR320,320_.jpg"},
  {id:13, title:"Crime and Punishment", genre:"Crime", rating:9.1, img:"https://images-na.ssl-images-amazon.com/images/I/81rcMSaAnRL._AC_UL320_SR320,320_.jpg"},
  {id:14, title:"Brave New World", genre:"Dystopian", rating:8.9, img:"https://images-na.ssl-images-amazon.com/images/I/81zJ9qF2mLL._AC_UL320_SR320,320_.jpg"},
  {id:15, title:"The Alchemist", genre:"Adventure", rating:9.0, img:"https://images-na.ssl-images-amazon.com/images/I/71aFt4+OTOL._AC_UL320_SR320,320_.jpg"},
  {id:16, title:"Gone with the Wind", genre:"Historical Fiction", rating:8.6, img:"https://images-na.ssl-images-amazon.com/images/I/91B7AUp9oDL._AC_UL320_SR320,320_.jpg"},
  {id:17, title:"The Perks of Being a Wallflower", genre:"Young Adult Fiction", rating:8.5, img:"https://images-na.ssl-images-amazon.com/images/I/81aY0uTJL2L._AC_UL320_SR320,320_.jpg"},
  {id:18, title:"The Little Prince", genre:"Children's Literature", rating:8.7, img:"https://images-na.ssl-images-amazon.com/images/I/71OZY035QKL._AC_UL320_SR320,320_.jpg"},
  {id:19, title:"The Da Vinci Code", genre:"Mystery Thriller", rating:7.9, img:"https://images-na.ssl-images-amazon.com/images/I/91Q5dCjc2ML._AC_UL320_SR320,320_.jpg"},
  {id:20, title:"Alice's Adventures in Wonderland", genre:"Fantasy Children's Literature", rating:8.1, img:"https://images-na.ssl-images-amazon.com/images/I/91f+U5Zf3TL._AC_UL320_SR320,320_.jpg"}
];
let reviews = [];
function saveData() {
  localStorage.setItem('movies', JSON.stringify(movies));
  localStorage.setItem('books', JSON.stringify(books));
  localStorage.setItem('reviews', JSON.stringify(reviews));
}
let users = JSON.parse(localStorage.getItem('users')) || [];
let currentUser = localStorage.getItem('currentUser') || "";
function showLoginModal(){document.getElementById('login-modal').style.display = 'flex';}
function hideLoginModal(){document.getElementById('login-modal').style.display = 'none';document.getElementById('login-error').innerText='';}
function login(e){
  e.preventDefault();
  const form = e.target;
  const uname = form.username.value.trim(), pass = form.password.value.trim();
  let user = users.find(u=>u.uname===uname);
  if(!user){
    users.push({uname, pass});
    localStorage.setItem('users', JSON.stringify(users));
    user = {uname, pass};
  }
  if(user.pass !== pass){
    document.getElementById('login-error').innerText = "Invalid password!";
    return;
  }
  currentUser = uname;
  localStorage.setItem('currentUser', uname);
  hideLoginModal();
  renderUserInfo();
  navigate(location.hash);
}
function renderUserInfo() {
  const userInfo = document.getElementById('user-info');
  const loginBtn = document.getElementById('login-btn');
  const logoutBtn = document.getElementById('logout-btn');
  if (currentUser) {
    userInfo.innerText = `Logged in: ${currentUser}`;
    loginBtn.style.display = "none";
    logoutBtn.style.display = "inline-block";
  } else {
    userInfo.innerText = "";
    loginBtn.style.display = "inline-block";
    logoutBtn.style.display = "none";
  }
}
function logoutUser() {
  currentUser = "";
  localStorage.removeItem('currentUser');
  renderUserInfo();
  navigate("#home");
}
function showSpinner(){main.innerHTML = `<div class="spinner"></div>`;}
function showError(msg){main.innerHTML = `<div style="color:red;text-align:center;margin:2rem;">${msg}</div>`;}
const main = document.getElementById('main-content');
function navigate(hash){
  showSpinner();
  setTimeout(() => {
    switch(hash){
      case '#movies': renderMoviesPage(); break;
      case '#books': renderBooksPage(); break;
      case '#reviews': renderReviewsPage(); break;
      case '#admin': renderAdminPage(); break;
      default: renderHomePage(); break;
    }
  }, 300);
}
window.addEventListener('hashchange', ()=>navigate(location.hash)); navigate(location.hash);
renderUserInfo();

function calcAverageRating(type, id, defaultRating) {
  let list = reviews.filter(r => r.type === type && r.id === id);
  if (list.length === 0) return Number(defaultRating).toFixed(1);
  let avg = list.map(r => Number(r.rating)).reduce((a,b)=>a+b,0) / list.length;
  return avg.toFixed(1);
}

function renderSearchBar(type){
  return `
    <form onsubmit="searchItems(event, '${type}')">
      <input aria-label="Search ${type}" name="query" placeholder="Search title..." />
      <select name="genre"><option value="">All genres</option>
        ${(type==='movies'?movies:books)
          .map(x=>x.genre).filter((v,i,a)=>a.indexOf(v)==i).map(g=>`<option>${g}</option>`).join('')}
      </select>
      <select name="sort"><option value="">Sort By</option><option value="rating">Rating</option><option value="alpha">A-Z</option></select>
      <button type="submit">Go</button>
    </form>
  `;
}
function searchItems(e, type){
  e.preventDefault();
  let items = type==='movies'?movies:books;
  const {query, genre, sort} = e.target;
  let filtered = items.filter(x=>(
    (query.value === '' || x.title.toLowerCase().includes(query.value.toLowerCase())) &&
    (genre.value === '' || x.genre === genre.value)));
  if(sort.value==='rating') filtered.sort((a,b)=>parseFloat(calcAverageRating(type,a.id,a.rating))-parseFloat(calcAverageRating(type,b.id,b.rating))).reverse();
  if(sort.value==='alpha') filtered.sort((a,b)=>a.title.localeCompare(b.title));
  type==='movies'?renderMoviesPage(filtered):renderBooksPage(filtered);
}

function renderHomePage(){
  main.innerHTML = `
    <section>
      <h2>Top Rated Movies</h2>
      <div class='card-container'>${movies.slice(0,5).map(m=>cardMarkup(m,'movie')).join('')}</div>
    </section>
    <section>
      <h2>Top Rated Books</h2>
      <div class='card-container'>${books.slice(0,5).map(b=>cardMarkup(b,'book')).join('')}</div>
    </section>
  `;
}
function renderMoviesPage(filtered=null){
  let list = filtered || movies;
  main.innerHTML = `<h2>Movies</h2>${renderSearchBar('movies')}<div class='card-container'>${list.map(m=>cardMarkup(m,'movie')).join('')}</div>`;
}
function renderBooksPage(filtered=null){
  let list = filtered || books;
  main.innerHTML = `<h2>Books</h2>${renderSearchBar('books')}<div class='card-container'>${list.map(b=>cardMarkup(b,'book')).join('')}</div>`;
}
function cardMarkup(item, type){
  return `<div class='card' tabindex="0" aria-label="View ${item.title}" onclick='viewItem("${type}",${item.id})' onkeypress="if(event.key==='Enter'){viewItem('${type}',${item.id})}">
    <img src='${item.img}' alt="${item.title} cover" onerror='this.src="https://via.placeholder.com/180x270?text=Image+Not+Found"'>
    <div class='info'>
      <h3>${item.title}</h3>
      <p>${item.genre}</p>
      <p>Rating: <span class='rating-span'>${calcAverageRating(type,item.id,item.rating)}</span></p>
    </div>
  </div>`;
}
function viewItem(type, id){
  const arr = type==='movie'?movies:books;
  const x = arr.find(i=>i.id===id);
  if(!x){showError("Not found!");return;}
  main.innerHTML = `<h2>${x.title}</h2>
    <img src='${x.img}' style='width:200px' alt='${x.title} cover' onerror='this.src="https://via.placeholder.com/200x300?text=Image+Not+Found"'>
    <p>Genre: ${x.genre}</p>
    <p>Average Rating: <span class="rating-span">${calcAverageRating(type, id, x.rating)}</span></p>
    <h3>Reviews</h3>
    ${renderReviews(type, id)}
    <h4>Add Review</h4>
    ${renderReviewForm(type, id)}`;
}
function renderReviews(type,id){
  let list = reviews.filter(r=>r.type===type && r.id===id);
  if(!list.length) return '<p>No reviews yet.</p>';
  return list.map((r,i)=>`<p>${r.text} - Rating: ${r.rating} <br><span>By: ${r.user||'Anonymous'}</span> <button onclick='deleteReview(${i})' aria-label='Delete review'>Delete</button></p>`).join('');
}
function renderReviewForm(type,id){
  if(!currentUser) return `<p>Please <a href="#" onclick="showLoginModal()">login</a> to add a review.</p>`;
  return `<form onsubmit='addReview(event,"${type}",${id})'>
      <label for='rating'>Rating:</label>
      <select name='rating' id='rating'><option>1</option><option>2</option><option>3</option><option>4</option><option>5</option></select>
      <label for='text'>Review:</label>
      <textarea name='text' id='text' required aria-label="Review text"></textarea>
      <button type='submit'>Submit</button>
    </form>`;
}
function addReview(e,type,id){
  e.preventDefault();
  if(!currentUser){alert("Login first");return;}
  const form = e.target;
  const text = form.text.value, rating = form.rating.value;
  reviews.push({type,id,text,rating,user:currentUser});
  saveData();
  navigate(location.hash);
}
function deleteReview(index){
  reviews.splice(index,1);
  saveData();
  navigate(location.hash);
}
function renderReviewsPage(){
  main.innerHTML = `<h2>All Reviews</h2>
    ${reviews.length===0?'<p>No reviews submitted.</p>':
    '<table><tr><th>Type</th><th>Title</th><th>Review</th><th>Rating</th><th>User</th></tr>'+
    reviews.map(r=>`<tr>
      <td>${r.type}</td>
      <td>${r.type==='movie'?movies.find(m=>m.id===r.id)?.title:books.find(b=>b.id===r.id)?.title}</td>
      <td>${r.text}</td>
      <td>${r.rating}</td>
      <td>${r.user||'Anonymous'}</td></tr>`).join('')+'</table>'
    }`;
}
function renderAdminPage() {
  if (!currentUser) {
    main.innerHTML = `<h2>Admin Dashboard</h2>
      <div style="color:#736EFE;font-size:1.2rem;margin:2rem 0;">
        Please log in to manage movies and books.
      </div>`;
    return;
  }
  main.innerHTML = `
    <h2>Admin Dashboard</h2>
    <h3>Movies</h3>
    <button onclick='addMoviePrompt()'>Add Movie</button>
    <table>
      <tr><th>Title</th><th>Genre</th><th>Avg Rating</th><th>Actions</th></tr>
      ${movies.map((m,i) =>
        `<tr>
          <td>${m.title}</td>
          <td>${m.genre}</td>
          <td><span class="rating-span">${calcAverageRating('movie',m.id,m.rating)}</span></td>
          <td>
            <button onclick='editMovie(${i})'>Edit</button>
            <button onclick='deleteMovie(${i})'>Delete</button>
          </td>
        </tr>`).join('')}
    </table>
    <h3>Books</h3>
    <button onclick='addBookPrompt()'>Add Book</button>
    <table>
      <tr><th>Title</th><th>Genre</th><th>Avg Rating</th><th>Actions</th></tr>
      ${books.map((b,i) =>
        `<tr>
          <td>${b.title}</td>
          <td>${b.genre}</td>
          <td><span class="rating-span">${calcAverageRating('book',b.id,b.rating)}</span></td>
          <td>
            <button onclick='editBook(${i})'>Edit</button>
            <button onclick='deleteBook(${i})'>Delete</button>
          </td>
        </tr>`).join('')}
    </table>
  `;
}


function addMoviePrompt(){
  const title=prompt('Title:'), genre=prompt('Genre:'), rating=prompt('Rating:'), img=prompt('Image URL:');
  if(title && genre && rating && img) movies.push({id:Date.now(),title,genre,rating:parseFloat(rating),img});
  saveData(); renderAdminPage();
}
function editMovie(i){
  const m=movies[i];
  const title=prompt('Title:',m.title), genre=prompt('Genre:',m.genre), rating=prompt('Rating:',m.rating), img=prompt('Image URL:',m.img);
  if(title && genre && rating && img) movies[i]={...m,title,genre,rating:parseFloat(rating),img};
  saveData(); renderAdminPage();
}
function deleteMovie(i){
  if(confirm('Delete this movie?')){
    const id = movies[i].id;
    movies.splice(i,1);
    reviews = reviews.filter(r => !(r.type === 'movie' && r.id === id));
    saveData();
    renderAdminPage();
  }
}
function addBookPrompt(){
  const title=prompt('Title:'), genre=prompt('Genre:'), rating=prompt('Rating:'), img=prompt('Image URL:');
  if(title && genre && rating && img) books.push({id:Date.now(),title,genre,rating:parseFloat(rating),img});
  saveData(); renderAdminPage();
}
function editBook(i){
  const b=books[i];
  const title=prompt('Title:',b.title), genre=prompt('Genre:',b.genre), rating=prompt('Rating:',b.rating), img=prompt('Image URL:',b.img);
  if(title && genre && rating && img) books[i]={...b,title,genre,rating:parseFloat(rating),img};
  saveData(); renderAdminPage();
}
function deleteBook(i){
  if(confirm('Delete this book?')){
    const id = books[i].id;
    books.splice(i,1);
    reviews = reviews.filter(r => !(r.type === 'book' && r.id === id));
    saveData();
    renderAdminPage();
  }
}
</script>
</body>
</html>
