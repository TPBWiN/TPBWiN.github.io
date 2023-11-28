<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Starry Content Page</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: black;
            color: white;
            font-family: 'Roboto', sans-serif;
        }

        #content-container {
            z-index: 1;
            position: relative;
            text-align: center;
        }

        .activation-key {
            margin-bottom: 10px;
            position: relative;
        }

        .copy-button {
            cursor: pointer;
            background-color: #4CAF50; /* Green background */
            color: white;
            border: none;
            border-radius: 3px;
            transition: background-color 0.3s;
            padding: 5px 10px;
            font-size: 14px;
            position: absolute;
            top: 50%;
            right: 5%;
            transform: translate(50%, -50%);
        }

        .copy-button:hover {
            background-color: #45a049; /* Darker green on hover */
        }

        .activation-key p {
            display: inline-block;
            margin-right: 10px; /* Adjust the margin as needed */
            font-weight: 700; /* Bold */
        }

        .star {
            position: absolute;
            width: 2px;
            height: 2px;
            background: white;
        }
    </style>
</head>
<body>
    <div id="content-container"></div>

    <script>
        // Function to generate a random number between min and max
        function getRandomNumber(min, max) {
            return Math.random() * (max - min) + min;
        }

        // Generate content dynamically
        const contentContainer = document.getElementById('content-container');
        const contentArray = [
            "MV6RH-AR2DM-0J151-1C17P-1ARKF",
            "4F6N2-45H80-MJ409-1H0XP-2G066",
            "1Z4XR-4ZH4M-HJ0A9-0L3Z6-8P8P8",
            // ... add more content items here
        ];

        for (let i = 0; i < contentArray.length; i++) {
            const contentItem = document.createElement('div');
            contentItem.className = 'activation-key';

            const keyText = document.createElement('p');
            keyText.textContent = contentArray[i];

            const copyButton = document.createElement('button');
            copyButton.className = 'copy-button';
            copyButton.textContent = 'Copy';
            copyButton.addEventListener('click', function () {
                // Copy the activation key to the clipboard
                navigator.clipboard.writeText(contentArray[i]);
            });

            contentItem.appendChild(keyText);
            contentItem.appendChild(copyButton);
            contentContainer.appendChild(contentItem);
        }

        // Generate moving stars dynamically
        const starsContainer = document.createElement('div');
        starsContainer.style.position = 'fixed';
        starsContainer.style.top = '0';
        starsContainer.style.left = '0';
        starsContainer.style.width = '100%';
        starsContainer.style.height = '100%';
        document.body.appendChild(starsContainer);

        const numStars = 50;

        for (let i = 0; i < numStars; i++) {
            const star = document.createElement('div');
            star.className = 'star';
            starsContainer.appendChild(star);

            animateStar(star);
        }

        function animateStar(star) {
            const speed = getRandomNumber(1, 5);
            const xPos = getRandomNumber(0, window.innerWidth);
            const yPos = getRandomNumber(0, window.innerHeight);

            star.style.left = `${xPos}px`;
            star.style.top = `${yPos}px`;

            function moveStar() {
                const currentX = parseFloat(star.style.left);
                const currentY = parseFloat(star.style.top);

                star.style.left = `${currentX + speed}px`;

                if (currentX > window.innerWidth) {
                    star.style.left = `0px`;
                    star.style.top = `${getRandomNumber(0, window.innerHeight)}px`;
                }

                requestAnimationFrame(moveStar);
            }

            moveStar();
        }
    </script>
</body>
</html>
