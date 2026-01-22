        #chatbot {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 300px;
            height: 400px;
            border: 1px solid #ccc;
            background: white;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            display: flex;
            flex-direction: column;
        }
        #chat-messages {
            flex: 1;
            padding: 10px;
            overflow-y: auto;
        }
        #chat-input {
            display: flex;
            padding: 10px;
        }
        #chat-input input {
            flex: 1;
            margin-right: 5px;
        }
        .message {
            margin-bottom: 10px;
        }
        .user { text-align: right; color: blue; }
        .bot { text-align: left; color: green; }
        </head>
<body>
    <!-- Intégrez ce div dans votre site web -->
    <div id="chatbot">
        <div id="chat-messages"></div>
        <div id="chat-input">
            <input type="text" id="user-input" placeholder="Posez votre question...">
            <button onclick="sendMessage()">Envoyer</button>
        </div>
    </div>

    <script>
        function addMessage(text, className) {
            const messages = document.getElementById('chat-messages');
            const message = document.createElement('div');
            message.className = 'message ' + className;
            message.textContent = text;
            messages.appendChild(message);
            messages.scrollTop = messages.scrollHeight;
        }

        function sendMessage() {
            const input = document.getElementById('user-input');
            const question = input.value.trim().toLowerCase();
            if (!question) return;

            addMessage(question, 'user');
            input.value = '';

            // Réponses basées sur des mots-clés
            let response = "Désolé, je n'ai pas compris votre question. Pouvez-vous reformuler ?";
            
            if (question.includes('adresse')) {
                response = "L'adresse du lycée est : 2, quai des Pêcheurs, 67500 Haguenau.";
            } else if (question.includes('téléphone') || question.includes('tel')) {
                response = "Le numéro de téléphone est : 03 88 07 44 00.";
            } else if (question.includes('email') || question.includes('courriel')) {
                response = "Pour les absences : vie-scolaire1.0670020H@ac-strasbourg.fr. Pour d'autres contacts, veuillez consulter le site.";
            } else if (question.includes('inscriptions') || question.includes('inscription')) {
                response = "Les dossiers d'inscriptions pour la rentrée 2025 sont disponibles en juin. Consultez la page inscriptions sur le site.";
            } else if (question.includes('formations') || question.includes('programmes')) {
                response = "Le lycée propose des filières générales, technologiques (STL, ST2S), options comme Arts Plastiques, Langues, Maths, et des sections européennes et internationales (Abibac, Euro Anglais-Histoire). Il y a aussi des formations post-bac.";
            } else if (question.includes('portes ouvertes')) {
                response = "La Journée Portes Ouvertes est prévue le samedi 7 février de 8h15 à 12h. Consultez l'affiche sur le site.";
            } else if (question.includes('menu') || question.includes('cantine')) {
                response = "Le menu de la semaine est disponible en PDF sur le site.";
            } else if (question.includes('vacances') || question.includes('congés')) {
                response = "Les dates des vacances scolaires sont disponibles en PDF sur le site.";
            } else if (question.includes('actualités') || question.includes('news')) {
                response = "Dernières actualités : Accueil d'élèves allemands, Voyage à Munich, Remise des diplômes le 22 novembre 2025, etc. Visitez la page d'accueil pour plus.";
            } else if (question.includes('bonjour') || question.includes('salut')) {
                response = "Bonjour ! Comment puis-je vous aider concernant le Lycée Robert Schuman ?";
            }

            setTimeout(() => addMessage(response, 'bot'), 500);
        }

        // Message de bienvenue
        addMessage("Bonjour ! Je suis le chatbot du Lycée Robert Schuman. Posez-moi des questions sur l'adresse, les contacts, les formations, etc.", 'bot');
    </script>
</body>
</html>
