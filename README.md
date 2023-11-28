<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            margin: 0;
            overflow: hidden;
        }

        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }

        .star {
            position: absolute;
            background: white;
            border-radius: 50%;
            animation: twinkle linear infinite;
        }

        @keyframes twinkle {
            0%, 100% {
                opacity: 0.8;
            }
            50% {
                opacity: 0.4;
            }
        }

        .content-container {
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            color: white;
            font-size: 24px;
        }
    </style>
    <title>Starry Content Page</title>
</head>
<body>
    <div class="stars"></div>
    <div class="content-container" id="content-container">
        <!-- Content will be dynamically generated here -->
    </div>

    <script>
        // Generate stars dynamically
        const starsContainer = document.querySelector('.stars');
        const numStars = 50;

        for (let i = 0; i < numStars; i++) {
            const star = document.createElement('div');
            star.className = 'star';
            star.style.width = `${Math.random() * 3}px`;
            star.style.height = star.style.width;

            const xPos = Math.random() * 100;
            const yPos = Math.random() * 100;

            star.style.left = `${xPos}vw`;
            star.style.top = `${yPos}vh`;

            starsContainer.appendChild(star);
        }

        // Generate content dynamically
        const contentContainer = document.getElementById('content-container');
        const contentArray = [
            "5G44H-ACH50-0J4C9-1VC5P-CY0QD",
            "JC000-8G047-MJDF1-0H3E6-8QR5F",
            "JV2NU-0XL5N-0J4Q8-0T0E6-8GH56",
            // ... add more content items here
        ];

        for (let i = 0; i < 5000; i++) {
            const contentItem = document.createElement('p');
            contentItem.textContent = contentArray[i % contentArray.length];
            contentContainer.appendChild(contentItem);
        }
    </script>
</body>
</html>
