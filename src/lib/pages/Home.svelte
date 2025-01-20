<script>
    import logoCars from "../../assets/pictures/logoCars.svg"
</script>

<section id="home">
    <section class="presentation">
        <div class="presentation-text">
            <h1>Amaury Madani, expert automobile</h1>
            <p>Fort de plusieurs années d’expérience, je met mon savoir-faire au service des <strong>automobilistes</strong> avec une approche à la fois humaine et professionnelle.<br><br> Passionné par l’<strong>automobile</strong> et animé par une volonté d’offrir un accompagnement personnalisé, je m’engage à analyser chaque situation avec rigueur et transparence. Grâce à une <strong>expertise</strong> technique pointue, il intervient dans des domaines variés tels que les <strong>litiges</strong>, les évaluations de dommages ou encore les conseils pour l’achat et la vente de véhicules.<br><br>Attentif aux besoins de ses clients, Amaury Madani privilégie toujours un dialogue clair et constructif, afin d’apporter des solutions adaptées et de garantir leur satisfaction. Confier votre <strong>véhicule</strong> à Amaury Madani, c’est faire le choix d’un expert à l’écoute, pour qui chaque détail compte.</p>
        </div>
        <div class="presentation-valeurs">
            <h2>Nos Valeurs</h2>
            <ul>
                <li>Impartialité</li>
                <li>Intégrité</li>
                <li>indépendance</li>
                <li>Excellence</li>
            </ul>
        </div>
    </section>

    <section class="services">
        <h2>Nos Services</h2>
        <ul>
            <li>Partenariat juridique : <br> Lorem ipsum dolor sit amet .</li>
            <li>Blablabla : <br> Lorem ipsum dolor sit amet consectetur adipisicing elit.</li>
            <li>Blablabla2 : <br> Dolor sit amet consectetur adipisicing elit.</li>
            <li>... : <br> Lorem ipsum dolor sit amet consectetur adipisicing elit.</li>
        </ul>
    </section>
    
    <section class="logoVehicules">
        <img src={logoCars} alt="Voiture citadine">
    </section>
    
    <section class="faq">
        <h2>FAQ</h2>
        <div class="accordeon">
            <p aria-hidden="true">↓</p>
            <h4>Dans quel contexte faire appel à un expert automobile ?</h4>
            <p>En cas d’accident pour évaluer les dommages subis par votre véhicule et déterminer le coût des réparations. Pour vérifier l’état général d’un véhicule ou évaluer la valeur d’un véhicule lors d’un achat en vérifiant qu’il ne présente pas de vices cachés. En cas de litiges ou désaccord ou un soupçon de fraude. </p>
        </div>
        <div class="accordeon">
            <p aria-hidden="true">↓</p>
            <h4>Dans quel contexte faire appel à un expert automobile ?</h4>
            <p>En cas d’accident pour évaluer les dommages subis par votre véhicule et déterminer le coût des réparations. Pour vérifier l’état général d’un véhicule ou évaluer la valeur d’un véhicule lors d’un achat en vérifiant qu’il ne présente pas de vices cachés. En cas de litiges ou désaccord ou un soupçon de fraude. </p>
        </div>
        <div class="accordeon">
            <p aria-hidden="true">↓</p>
            <h4>Dans quel contexte faire appel à un expert automobile ?</h4>
            <p>En cas d’accident pour évaluer les dommages subis par votre véhicule et déterminer le coût des réparations. Pour vérifier l’état général d’un véhicule ou évaluer la valeur d’un véhicule lors d’un achat en vérifiant qu’il ne présente pas de vices cachés. En cas de litiges ou désaccord ou un soupçon de fraude. </p>
        </div>
    </section>
    
    <section class="formulaire">
        <h2>Formulaire de contact</h2>
        <form action="" method="post">
            <label for="demande">Quel est votre demande ?</label>
            <select name="demande" id="demande" required>
                <option value="information">Je souhaite avoir une information</option>
                <option value="Expertise">Expertise véhicule</option>
                <option value="autre">Autre</option>
            </select>
    
            <label>Est-elle urgente ?</label>
            <input type="radio" name="urgence" id="oui" value="oui">
            <label for="oui">Oui</label>
            <input type="radio" name="urgence" id="non" value="non">
            <label for="non">Non</label>
    
            <label for="location">Localisation de votre besoin ?</label>
            <select name="localisation" id="localisation" required>
                <option value="Montpellier">Montpellier</option>
                <option value="Bouches-du-Rhône">Bouches-du-Rhône</option>
                <option value="Var">Var</option>
                <option value="Gard">Gard</option>
                <option value="Hérault">Hérault</option>
            </select>
    
            <label for="nom">Votre nom</label>
            <input type="text" name="nom" id="nom" required>
    
            <label for="tel">Votre numéro de téléphone</label>
            <input type="tel" pattern="^0[1-9]( [0-9]{2}){4}$" placeholder="01.02.03.04.05" name="tel" id="tel">
    
            <label for="email">Votre e-mail</label>
            <input type="email" name="email" id="email" placeholder="example@gmail.com">
    
            <label for="commentaire">Un commentaire</label>
            <textarea name="commentaire" id="commentaire" required></textarea>
    
            <buttton type="submit">Envoyer</buttton>
        </form>
    </section>
</section>

<style lang="scss">
    #home {
        padding: 1rem;

        .presentation {

            &-text {
                background-color: white;
                border-radius: 0.625rem;
                padding: 1rem;
                margin-bottom: 1rem;

                h1 {
                    padding-bottom: 0.5rem;
                }

                // p:first-of-type {
                //     text-indent: 0.8rem; /* Indente la première ligne du premier paragraphe */
                // }
            }

            &-valeurs {
                background-color: white;
                border-radius: 0.625rem;
                padding: 1rem;
                margin-bottom: 1rem;

                h2 {
                    padding-bottom: 0.5rem;
                    text-align: center;
                }

                ul {
                    display: flex;
                    justify-content: center;
                    flex-wrap: wrap;
                    list-style-type: disc;
                    padding-left: 1rem;


                    li {
                        width: 50%;
                        list-style-type: inherit; 
                    }
                }
            }
        }

        .services {
            background-color: white;
            border-radius: 0.625rem;
            padding: 1rem;
            margin-bottom: 1rem;

            h2 {
                padding-bottom: 0.5rem;
                text-align: center;
            }

            ul {
                display: flex;
                justify-content: center;
                flex-wrap: wrap;
                list-style-type: disc;
                padding-left: 1rem;

                li {
                    width: 50%;
                    list-style-type: inherit; 
                }
            }
        }

        .logoVehicules {
            margin-bottom: 1rem;

            img {
                width: 18rem;
            }
        }

        .faq {
            background-color: white;
            border-radius: 0.625rem;
            padding: 1rem;
            margin-bottom: 1rem;

            h2 {
                padding-bottom: 0.5rem;
                text-align: center;
            }

            .accordeon {
                border: 0.15rem solid var(--faqLogo);
                border-radius: 0.625rem;
                padding: 0.5rem;
                margin-bottom: 0.5rem;

                p {
                    text-align: center;
                    cursor: pointer;
                }

                h4 {
                    padding-bottom: 0.5rem;
                }

                p:last-of-type {
                    display: none;
                }

                p[aria-hidden="false"] + h4 + p {
                    display: block;
                }
            }
        }
    }   
</style>