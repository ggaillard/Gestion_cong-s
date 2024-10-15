<!-----



Conversion time: 0.832 seconds.


Using this HTML file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β40
* Tue Oct 15 2024 13:10:06 GMT-0700 (PDT)
* Source doc: Séance d'entrainement 4
----->


<h1>Séance d'Entraînement Symfony</h1>


<h2>Objectif</h2>


<p>
Créer un projet Symfony de A à Z pour gérer les jours de congés de l'entreprise BTS-SIO-SLAM.
</p>
<h2>Prérequis</h2>


<ul>

<li>PHP >= 7.2.5</li>

<li>Composer</li>

<li>Symfony CLI</li>

<li>Un éditeur de code (par exemple, VSCode)</li>
</ul>
<h2>Étapes</h2>


<h3>1. Installation de Symfony CLI</h3>


<p>
Téléchargez et installez Symfony CLI depuis <a href="https://symfony.com/download">le site officiel</a>.
</p>
<h3>2. Création du Projet</h3>


<p>
Ouvrez votre terminal et exécutez la commande suivante :
</p>
<p>
symfony new gestion_conges --full
</p>
<h3>3. Configuration de l'environnement</h3>


<p>
Naviguez dans le répertoire du projet :
</p>
<p>
cd gestion_conges
</p>
<p>
Copiez le fichier <code>.env</code> en <code>.env.local</code> et configurez vos paramètres de base de données.
</p>
<h3>4. Installation des dépendances</h3>


<p>
Assurez-vous que toutes les dépendances sont installées :
</p>
<p>
composer install
</p>
<h3>5. Configuration de PostgreSQL avec Symfony</h3>


<h4>5.1. Installer PostgreSQL</h4>


<p>
Si PostgreSQL n'est pas déjà installé, téléchargez l'installateur depuis <a href="https://www.postgresql.org/download/">PostgreSQL Downloads</a>.
</p>
<h4>5.2. Installer l'extension <code>pdo_pgsql</code> pour PHP</h4>


<p>
Assurez-vous que l'extension <code>pdo_pgsql</code> est installée et activée. Sur Windows, modifiez le fichier <code>php.ini</code> pour décommenter :
</p>
<p>
extension=pdo_pgsql
</p>
<h4>5.3. Configurer la connexion PostgreSQL dans Symfony</h4>


<p>
Modifiez le fichier <code>.env.local</code> pour ajouter les détails de connexion à PostgreSQL :
</p>
<p>
DATABASE_URL="postgresql://username:password@127.0.0.1:5432/gestion_conges"
</p>
<p>
Remplacez <code>username</code> et <code>password</code> par vos informations d'identification PostgreSQL.
</p>
<h4>5.4. Créer la base de données</h4>


<p>
Exécutez la commande suivante :
</p>
<p>
php bin/console doctrine:database:create
</p>
<h3>6. Création des entités</h3>


<h4>6.1. Création de l'entité Utilisateur</h4>


<p>
Générez une entité Utilisateur :
</p>
<p>
php bin/console make:entity User
</p>
<p>
Ajoutez les champs suivants : <code>id</code>, <code>nom</code>, <code>prenom</code>, <code>email</code>, <code>password</code>.
</p>
<p>
Vous pouvez également créer l'entité en une seule commande :
</p>
<p>
php bin/console make:entity User --fields="nom:string,email:string,password:string"
</p>
<h4>6.2. Création de l'entité Congé</h4>


<p>
Générez une entité Congé :
</p>
<p>
php bin/console make:entity Conge
</p>
<p>
Ajoutez les champs suivants : <code>id</code>, <code>dateDebut</code>, <code>dateFin</code>, <code>type</code>, <code>status</code>, <code>user</code> (relation avec l'entité User).
</p>
<p>
Utilisez cette commande pour créer l'entité rapidement :
</p>
<p>
php bin/console make:entity Conge --fields="dateDebut:datetime,dateFin:datetime,type:string,user:relation:ManyToOne"
</p>
<h3>7. Création des contrôleurs</h3>


<h4>7.1. Création du <code>UserController</code></h4>


<p>
Générez un contrôleur pour gérer les utilisateurs :
</p>
<p>
php bin/console make:controller UserController
</p>
<p>
Ajoutez des routes et actions pour créer, lire, mettre à jour et supprimer des utilisateurs.
</p>
<h4>7.2. Création du <code>CongeController</code></h4>


<p>
Générez un contrôleur pour gérer les congés :
</p>
<p>
php bin/console make:controller CongeController
</p>
<h3>8. Configuration des routes</h3>


<p>
Pas besoin avec les attributs <code>#[Route('/conge', name: 'app_conge')]</code>. La route <code>/conge</code> est associée à une certaine action ou méthode dans le contrôleur, et elle est nommée <code>app_conge</code>. Cela permet de simplifier la configuration des routes en les définissant directement dans le code, plutôt que dans un fichier de configuration séparé.
</p>
<h3>9. Création des vues de base</h3>


<p>
Créez les vues suivantes :
</p>
<h4>Vue utilisateur</h4>


<p>
{# templates/user/index.html.twig #}
</p>
<p>
{% extends 'base.html.twig' %}
</p>
<p>
{% block title %}User{% endblock %}
</p>
<p>
{% block body %}
</p>
<p>
&lt;h1>User&lt;/h1>
</p>
<p>
{% endblock %}
</p>
<h4>Vue congé</h4>


<p>
{# templates/conge/index.html.twig #}
</p>
<p>
{% extends 'base.html.twig' %}
</p>
<p>
{% block title %}Congé{% endblock %}
</p>
<p>
{% block body %}
</p>
<p>
&lt;h1>Congé&lt;/h1>
</p>
<p>
{% endblock %}
</p>
<h3>10. Exécuter les migrations</h3>


<p>
Créez et exécutez les migrations pour la base de données :
</p>
<p>
php bin/console make:migration
</p>
<p>
php bin/console doctrine:migrations:migrate
</p>
<h3>11. Tester la base de données</h3>


<p>
Récupérez les noms de tables dans le schéma 'public' de la base de données :
</p>
<p>
php bin/console doctrine:query:sql "SELECT table_name FROM information_schema.tables WHERE table_schema = 'public';"
</p>
<h3>12. Installation de Symfony Foundry</h3>


<p>
Si ce n'est pas encore fait, installez Symfony Foundry, un outil pratique pour générer des entités et des données fictives :
</p>
<p>
composer require --dev orm-fixtures foundry
</p>
<h3>13. Générer la classe UserFactory</h3>


<p>
Après avoir installé Foundry, vous devez créer une factory pour votre entité User. Vous pouvez générer une factory avec la commande suivante :
</p>
<p>
php bin/console make:factory User
</p>
<h3>14. Lancement du serveur</h3>


<p>
Démarrez le serveur de développement Symfony :
</p>
<p>
symfony server:start
</p>
<p>
Accédez à votre application via <code>http://localhost:8000</code>.
</p>
<h3>15. CRUD pour la gestion des congés</h3>


<p>
Le projet inclut un système CRUD (Create, Read, Update, Delete) pour gérer les congés :
</p>
<h4>15.1. Créer un Congé</h4>


<ul>

<li><strong>Route</strong> : <code>/conge/new</code></li>

<li><strong>Action</strong> : Permet à un utilisateur de créer un nouveau congé via un formulaire.</li>
</ul>
<h4>15.2. Lire la liste des Congés</h4>


<ul>

<li><strong>Route</strong> : <code>/conge</code></li>

<li><strong>Action</strong> : Affiche une liste de tous les congés dans la base de données, incluant des liens pour modifier ou supprimer chaque congé.</li>
</ul>
<h4>15.3. Modifier un congé</h4>


<ul>

<li><strong>Route</strong> : <code>/conge/{id}/edit</code></li>

<li><strong>Action</strong> : Permet à un utilisateur de modifier un congé existant via un formulaire pré-rempli.</li>
</ul>
<h4>15.4. Supprimer un congé</h4>


<ul>

<li><strong>Route</strong> : <code>/conge/{id}/delete</code></li>

<li><strong>Action</strong> : Permet à un utilisateur de supprimer un congé après confirmation.</li>
</ul>
<h3>16. Création des vues de base</h3>


<p>
Créez les vues suivantes :
</p>
<h4>Vue utilisateur</h4>


<p>
{# templates/user/index.html.twig #}
</p>
<p>
{% extends 'base.html.twig' %}
</p>
<p>
{% block title %}User{% endblock %}
</p>
<p>
{% block body %}
</p>
<p>
&lt;h1>User&lt;/h1>
</p>
<p>
{% endblock %}
</p>
<h4>Vue congé</h4>


<p>
{# templates/conge/index.html.twig #}
</p>
<p>
{% extends 'base.html.twig' %}
</p>
<p>
{% block title %}Liste des Congés{% endblock %}
</p>
<p>
{% block body %}
</p>
<p>
&lt;h1>Liste des Congés&lt;/h1>
</p>
<p>
&lt;table class="table">
</p>
<p>
    &lt;thead>
</p>
<p>
        &lt;tr>
</p>
<p>
            &lt;th>Date début&lt;/th>
</p>
<p>
            &lt;th>Date fin&lt;/th>
</p>
<p>
            &lt;th>Type&lt;/th>
</p>
<p>
            &lt;th>Utilisateur&lt;/th>
</p>
<p>
            &lt;th>Actions&lt;/th>
</p>
<p>
        &lt;/tr>
</p>
<p>
    &lt;/thead>
</p>
<p>
    &lt;tbody>
</p>
<p>
    {% for conge in conges %}
</p>
<p>
        &lt;tr>
</p>
<p>
            &lt;td>{{ conge.dateDebut|date('Y-m-d') }}&lt;/td>
</p>
<p>
            &lt;td>{{ conge.dateFin|date('Y-m-d') }}&lt;/td>
</p>
<p>
            &lt;td>{{ conge.type }}&lt;/td>
</p>
<p>
            &lt;td>{{ conge.user.nom }}&lt;/td>
</p>
<p>
            &lt;td>
</p>
<p>
                &lt;a href="{{ path('conge_edit', {'id': conge.id}) }}">Modifier&lt;/a>
</p>
<p>
                &lt;form method="post" action="{{ path('conge_delete', {'id': conge.id}) }}" onsubmit="return confirm('Êtes-vous sûr de vouloir supprimer ce congé ?');">
</p>
<p>
                    &lt;input type="hidden" name="_token" value="{{ csrf_token('delete' ~ conge.id) }}">
</p>
<p>
                    &lt;button class="btn btn-danger">Supprimer&lt;/button>
</p>
<p>
                &lt;/form>
</p>
<p>
            &lt;/td>
</p>
<p>
        &lt;/tr>
</p>
<p>
    {% else %}
</p>
<p>
        &lt;tr>
</p>
<p>
            &lt;td colspan="5">Aucun congé trouvé&lt;/td>
</p>
<p>
        &lt;/tr>
</p>
<p>
    {% endfor %}
</p>
<p>
    &lt;/tbody>
</p>
<p>
&lt;/table>
</p>
<p>
&lt;a href="{{ path('conge_new') }}">Ajouter un nouveau congé&lt;/a>
</p>
<p>
{% endblock %}
</p>
<h3>17. Tests et débogage</h3>


<p>
Utilisez les outils de débogage intégrés et écrivez des tests pour vérifier le bon fonctionnement de votre application.
</p>
<h2>Conclusion</h2>


<p>
Vous avez maintenant un projet Symfony fonctionnel pour la gestion des jours de congés. Continuez à explorer les fonctionnalités de Symfony pour enrichir votre application.
</p>
<h3>License</h3>


<p>
Creative Commons pour le texte et MIT pour le code.
</p>
