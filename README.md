# CurserInteraction
Curser Interaction is an approach to create a rainbow effect follwing the curser as it moves accross the website.
This code is a landing page which I am currently working on for the curser to interact with your mouse 

<!DOCTYPE html>
<html lang="en">
<head>      
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cursor Interaction</title>
    <!-- Tailwind CSS CDN -->
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <!-- DaisyUI CDN -->
    <link href="https://cdn.jsdelivr.net/npm/daisyui@1.14.0/dist/full.css" rel="stylesheet">
    <style>
        body, html {
            padding: 0;
            margin: 0;
            overscroll-behavior: none;
            background-color: #000;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            position: relative;
            z-index: 1;
        }
        .card {
            border: none;
            border-radius: 1rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            background: rgba(255, 255, 255, 0.85); /* Slightly transparent background for the card */
        }
        .card-body {
            padding: 2rem;
        }
        .btn-primary {
            background-color: #007bff;
            border: none;
            border-radius: 25px;
            padding: 10px 20px;
        }
        .btn-primary:hover {
            background-color: #0056b3;
        }
        .form-control {
            border-radius: 25px;
        }
        .label-text {
            color: black;
        }
        .signup-text {
            text-align: center;
            margin-top: 1rem;
        }
        .signup-text a {
            color: #007bff;
            text-decoration: none;
        }
        .signup-text a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <canvas id="canvas"></canvas>
    <div class="container mx-auto p-4">
        <div class="max-w-md mx-auto bg-white rounded-xl shadow-md overflow-hidden md:max-w-2xl">
            <div class="md:flex">
                <div class="w-full p-4">
                    <div class="p-6 space-y-6">
                        <h2 class="text-2xl font-semibold text-center text-gray-700">Create Account</h2>
                        <form class="space-y-4">
                            <div class="form-control">
                                <label class="label">
                                    <span class="label-text">Full Name</span>
                                </label>
                                <input type="text" placeholder="John Doe" class="input input-bordered w-full" required>
                            </div>
                            <div class="form-control">
                                <label class="label">
                                    <span class="label-text">Email</span>
                                </label>
                                <input type="email" placeholder="example@example.com" class="input input-bordered w-full" required>
                            </div>
                            <div class="form-control">
                                <label class="label">
                                    <span class="label-text">Password</span>
                                </label>
                                <input type="password" placeholder="********" class="input input-bordered w-full" required>
                            </div>
                            <div class="form-control">
                                <label class="label">
                                    <span class="label-text">Confirm Password</span>
                                </label>
                                <input type="password" placeholder="********" class="input input-bordered w-full" required>
                            </div>
                            <div class="form-control mt-6">
                                <button class="btn btn-primary w-full">Sign Up</button>
                            </div>
                        </form>
                        <p class="text-center text-gray-500 mt-4">Already have an account? <a href="#" class="text-blue-500 hover:underline">Log in</a></p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Tailwind JS (optional, for interactivity) -->
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/custom-forms@0.3.4/dist/custom-forms.min.js"></script>
    
    <script>
        let mouseMoved = false;
        const pointer = {
            x: 0.5 * window.innerWidth,
            y: 0.5 * window.innerHeight,
        };

        const params = {
            pointsNumber: 40,
            widthFactor: 0.3,
            mouseThreshold: 0.6,
            spring: 0.4,
            friction: 0.5
        };

        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });

        window.addEventListener('mousemove', (e) => {
            pointer.x = e.clientX;
            pointer.y = e.clientY;
            mouseMoved = true;
        });

        function draw() {
            if (mouseMoved) {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                ctx.fillStyle = `rgba(${Math.random() * 255}, ${Math.random() * 255}, ${Math.random() * 255}, 0.5)`;
                ctx.beginPath();
                ctx.arc(pointer.x, pointer.y, 10, 0, Math.PI * 2);
                ctx.fill();
                mouseMoved = false;
            }
            requestAnimationFrame(draw);
        }

        draw();
    </script>
</body>
</html>
