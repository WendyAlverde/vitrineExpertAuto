<section class="error" role="document">
    <div class="error-content" role="alert">
        <h2>Oups ! Page non trouvée</h2>
        <p class="error-content-message">Désolé, la page que vous cherchez n'existe pas ou a été déplacée.</p>
        <a href="/" class="error-content-link">Retourner à l'accueil</a>
    </div>
</section>

<style lang="scss">
    .error {
        padding: 1rem;
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 65vh;
        background-color: var(--background);
        text-align: center;

        &-content {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            max-width: 500px;
            width: 100%;

            h2 {
                font-size: 2.5rem;
                color: #CF1F31;
                margin-bottom: 0.625rem;
            }

            &-message {
                font-size: 1.2rem;
                color: var(--text);
                margin-bottom: 20px;
            }

            &-link {
                font-size: 1.1rem;
                color: var(--backgroundComponents);
                text-decoration: none;
                padding: 10px 20px;
                border: 2px solid var(--form);
                border-radius: 4px;
                transition: background-color 0.3s ease;
            }

            &-link:hover {
                background-color: var(--form);
                color: white;
            }
        }
    }
</style>