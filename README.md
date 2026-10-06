body{
    font-family: Arial, sans-serif;
    margin:0;
    background:#f5f5f5;
}

/* Skip link */
.skip-link{
    position:absolute;
    left:-9999px;
}

.skip-link:focus{
    left:15px;
    top:15px;
    background:black;
    color:white;
    padding:10px;
}

/* Navigation */
.nav{
    display:flex;
    justify-content:center;
    gap:20px;
    list-style:none;
    background:navy;
    padding:20px;
}

.nav a{
    color:white;
    text-decoration:none;
    padding:10px 15px;
    border-radius:8px;
}

/* Hover requirement */
.nav a:hover{
    background:orange;
    transform:scale(1.1);
    transition:0.3s;
}

/* Images: Box Model */
img{
    width:300px;
    border:4px solid navy;
    padding:5px;
    border-radius:15px;
}

/* Grid requirement */
.gallery{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:20px;
    padding:20px;
}

/* nth-child requirement */
.gallery img:nth-child(even){
    border-radius:50%;
}

/* Flex requirement */
.skills{
    display:flex;
    justify-content:center;
    gap:15px;
}
