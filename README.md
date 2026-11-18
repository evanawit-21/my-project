
<!DOCTYPE html>
<html>
<head>
    <title>My Website</title>
</head>
<body>

    <h1>Welcome to My Website!</h1>

    <p>Hello! My name is Tsion.</p>

    <h2>About Me</h2>
    <p>Welcome to my personal website.</p>

    <h2>Contact Me</h2>
    <p>Email: evanawit2121@gmail.com.com</p>

<!DOCTYPE html>
<html>
<head>
    <title>My Website</title>
</head>
<body>

    <h1>Welcome to My Website!</h1>
    <p>Hello! My name is Tsion.</p>
    
    <h2>About Me</h2>
    <p>Welcome to my personal website.</p>
    
    <h2>Contact Me</h2>
    <p>Email: evanawit2121@gmail.com</p>

    <!-- ዳታቤዝ የሚልክ ፎርም -->
    <form id="userForm">
        <label>ስም:</label><br>
        <input type="text" id="name" required><br><br>
        
        <label>ኢሜይል:</label><br>
        <input type="email" id="email" required><br><br>
        
        <button type="submit">መዝግብ</button>
    </form>

    <!-- Firebase ኮድ -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
        import { getFirestore, collection, addDoc } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-firestore.js";

        const firebaseConfig = {
            apiKey: "YOUR_API_KEY",
            authDomain: "YOUR_AUTH_DOMAIN",
            projectId: "YOUR_PROJECT_ID"
        };

        const app = initializeApp(firebaseConfig);
        const db = getFirestore(app);

        const form = document.getElementById('userForm');
        form.addEventListener('submit', async (e) => {
            e.preventDefault();
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;

            try {
                await addDoc(collection(db, "users"), {
                    name: name,
                    email: email,
                    timestamp: new Date()
                });
                alert("መረጃው በተሳካ ሁኔታ ተመዝግቧል!");
                form.reset();
            } catch (e) {
                console.error("ስህተት ተፈጥሯል: ", e);
            }
        });
    </script>

</body>
</html></body>
</html>
