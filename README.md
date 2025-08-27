<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Albizia Mesures - Page Unique</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        .hidden { display: none; }
        @media print {
            body * { visibility: hidden; }
            .print-area, .print-area * { visibility: visible; }
            .print-area { position: absolute; left: 0; top: 0; }
            .no-print { display: none !important; }
        }
    </style>
</head>
<body class="bg-gray-100">

    <!-- En-tête -->
    <div class="bg-green-600 text-white p-6 no-print">
        <h1 class="text-2xl font-bold text-center">Albizia Mesures Pro</h1>
        <p class="text-center">Gestion des clients et matériaux</p>
    </div>

    <!-- Navigation -->
    <div class="bg-white shadow-lg sticky top-0 z-10 no-print">
        <div class="max-w-6xl mx-auto px-2">
            <nav class="flex overflow-x-auto">
                <button onclick="montrerSection('saisie')" id="btn-saisie" class="px-4 py-3 bg-green-600 text-white rounded-t">
                    Nouvelle Fiche
                </button>
                <button onclick="montrerSection('clients')" id="btn-clients" class="px-4 py-3 bg-gray-300 rounded-t">
                    Dossier Clients
                </button>
            </nav>
        </div>
    </div>

    <div class="container mx-auto p-4 max-w-6xl">

        <!-- Section Saisie Nouvelle Fiche -->
        <div id="section-saisie">

        <!-- Section Client -->
        <div class="bg-white rounded-lg shadow-lg p-6 mb-6">
            <h2 class="text-2xl font-bold mb-4">Informations Client</h2>
            
            <div class="grid md:grid-cols-2 gap-4">
                <div>
                    <label class="block font-bold mb-2">Nom du client *</label>
                    <input type="text" id="nom" class="w-full p-3 border rounded" placeholder="Nom et prénom">
                </div>
                <div>
                    <label class="block font-bold mb-2">Téléphone</label>
                    <input type="tel" id="telephone" class="w-full p-3 border rounded" placeholder="06 XX XX XX XX">
                </div>
                <div>
                    <label class="block font-bold mb-2">Email</label>
                    <input type="email" id="email" class="w-full p-3 border rounded" placeholder="email@exemple.fr">
                </div>
                <div>
                    <label class="block font-bold mb-2">Date</label>
                    <input type="date" id="date" class="w-full p-3 border rounded">
                </div>
            </div>
            
            <div class="mt-4">
                <label class="block font-bold mb-2">Adresse complète</label>
                <textarea id="adresse" class="w-full p-3 border rounded h-16" placeholder="Adresse complète du chantier"></textarea>
            </div>
        </div>

        <!-- Section Matériaux -->
        <div class="bg-white rounded-lg shadow-lg p-6 mb-6">
            <h2 class="text-2xl font-bold mb-4">Matériaux</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <!-- Autre matériau -->
                <div class="bg-gray-50 border border-gray-300 rounded-lg p-4">
                    <h3 class="font-bold mb-3 text-gray-800">Autre Matériau</h3>
                    <div>
                        <button onclick="ouvrir('autre-materiau')" class="w-full text-left p-2 hover:bg-gray-100 rounded">Autre matériau...</button>
                        <div id="autre-materiau" class="hidden mt-2 p-3 bg-white rounded border">
                            <input type="text" placeholder="Nom du matériau" class="w-full p-2 border rounded mb-2">
                            <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                            <select class="w-full p-2 border rounded mb-2">
                                <option value="m²">m²</option>
                                <option value="m³">m³</option>
                                <option value="ml">ml</option>
                                <option value="pièce">pièce</option>
                                <option value="kg">kg</option>
                                <option value="tonne">tonne</option>
                            </select>
                            <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                            <button onclick="ajouterAutre('autre-materiau')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                        </div>
                    </div>
                </div>

                <!-- Terrasses -->
                <div class="bg-yellow-50 border border-yellow-300 rounded-lg p-4">
                    <h3 class="font-bold mb-3 text-yellow-800">Terrasses</h3>
                    <div class="space-y-2">
                        <div>
                            <button onclick="ouvrir('terrasse-pin')" class="w-full text-left p-2 hover:bg-yellow-100 rounded">Terrasse Bois Pin</button>
                            <div id="terrasse-pin" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="m²">m²</option>
                                    <option value="ml">ml</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Terrasse Bois Pin', 'terrasse-pin')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                        <div>
                            <button onclick="ouvrir('terrasse-exotique')" class="w-full text-left p-2 hover:bg-yellow-100 rounded">Terrasse Bois Exotique</button>
                            <div id="terrasse-exotique" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="m²">m²</option>
                                    <option value="ml">ml</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Terrasse Bois Exotique', 'terrasse-exotique')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                        <div>
                            <button onclick="ouvrir('terrasse-ceramique')" class="w-full text-left p-2 hover:bg-yellow-100 rounded">Terrasse Céramique</button>
                            <div id="terrasse-ceramique" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="m²">m²</option>
                                    <option value="ml">ml</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Terrasse Céramique', 'terrasse-ceramique')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Allées -->
                <div class="bg-blue-50 border border-blue-300 rounded-lg p-4">
                    <h3 class="font-bold mb-3 text-blue-800">Allées</h3>
                    <div class="space-y-2">
                        <div>
                            <button onclick="ouvrir('allee-grouet')" class="w-full text-left p-2 hover:bg-blue-100 rounded">Allée Grouet</button>
                            <div id="allee-grouet" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="m²">m²</option>
                                    <option value="m³">m³</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Allée Grouet', 'allee-grouet')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                        <div>
                            <button onclick="ouvrir('allee-aplite')" class="w-full text-left p-2 hover:bg-blue-100 rounded">Allée Aplite</button>
                            <div id="allee-aplite" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="m²">m²</option>
                                    <option value="m³">m³</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Allée Aplite', 'allee-aplite')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                        <div>
                            <button onclick="ouvrir('gravier-030')" class="w-full text-left p-2 hover:bg-blue-100 rounded">0/30</button>
                            <div id="gravier-030" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="m³">m³</option>
                                    <option value="tonne">tonne</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('0/30', 'gravier-030')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bordures -->
                <div class="bg-purple-50 border border-purple-300 rounded-lg p-4">
                    <h3 class="font-bold mb-3 text-purple-800">Bordures</h3>
                    <div class="space-y-2">
                        <div>
                            <button onclick="ouvrir('bordure-acier')" class="w-full text-left p-2 hover:bg-purple-100 rounded">Bordure Acier</button>
                            <div id="bordure-acier" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="ml">ml</option>
                                    <option value="pièce">pièce</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Bordure Acier', 'bordure-acier')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                        <div>
                            <button onclick="ouvrir('bordure-pave')" class="w-full text-left p-2 hover:bg-purple-100 rounded">Bordure Pavé</button>
                            <div id="bordure-pave" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="ml">ml</option>
                                    <option value="pièce">pièce</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Bordure Pavé', 'bordure-pave')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Plantations -->
                <div class="bg-green-50 border border-green-300 rounded-lg p-4">
                    <h3 class="font-bold mb-3 text-green-800">Plantations</h3>
                    <div class="space-y-2">
                        <div>
                            <button onclick="ouvrir('arbres')" class="w-full text-left p-2 hover:bg-green-100 rounded">Arbres</button>
                            <div id="arbres" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="pièce">pièce</option>
                                    <option value="m²">m²</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Arbres', 'arbres')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                        <div>
                            <button onclick="ouvrir('gazon')" class="w-full text-left p-2 hover:bg-green-100 rounded">Gazon en rouleau</button>
                            <div id="gazon" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="m²">m²</option>
                                    <option value="pièce">pièce</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Gazon en rouleau', 'gazon')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Maçonnerie -->
                <div class="bg-orange-50 border border-orange-300 rounded-lg p-4">
                    <h3 class="font-bold mb-3 text-orange-800">Maçonnerie</h3>
                    <div class="space-y-2">
                        <div>
                            <button onclick="ouvrir('parpaing')" class="w-full text-left p-2 hover:bg-orange-100 rounded">Parpaing</button>
                            <div id="parpaing" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="pièce">pièce</option>
                                    <option value="m²">m²</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Parpaing', 'parpaing')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                        <div>
                            <button onclick="ouvrir('couvertine')" class="w-full text-left p-2 hover:bg-orange-100 rounded">Couvertine</button>
                            <div id="couvertine" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="ml">ml</option>
                                    <option value="pièce">pièce</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Couvertine', 'couvertine')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                        <div>
                            <button onclick="ouvrir('enduit')" class="w-full text-left p-2 hover:bg-orange-100 rounded">Enduit</button>
                            <div id="enduit" class="hidden mt-2 p-3 bg-white rounded border">
                                <input type="number" step="0.01" placeholder="Quantité" class="w-full p-2 border rounded mb-2">
                                <select class="w-full p-2 border rounded mb-2">
                                    <option value="m²">m²</option>
                                    <option value="kg">kg</option>
                                </select>
                                <textarea placeholder="Notes..." class="w-full p-2 border rounded mb-2 h-12"></textarea>
                                <button onclick="ajouter('Enduit', 'enduit')" class="w-full bg-green-600 text-white py-2 rounded hover:bg-green-700">Ajouter</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Matériaux Ajoutés -->
        <div class="bg-white rounded-lg shadow-lg p-6 mb-6">
            <h3 class="text-xl font-bold mb-4">Matériaux Renseignés</h3>
            <div id="liste-materiaux">
                <p class="text-gray-500 text-center py-4">Aucun matériau ajouté</p>
            </div>
        </div>

        <!-- Bouton de Validation -->
        <div class="bg-white rounded-lg shadow-lg p-6 mb-6 no-print text-center">
            <button onclick="valider()" class="bg-blue-600 text-white px-8 py-4 rounded-lg text-xl font-bold hover:bg-blue-700">
                Valider et Générer le Dossier Client
            </button>
        </div>

        <!-- Section Dossier Clients -->
        <div id="section-clients" class="hidden">
            <h2 class="text-2xl font-bold mb-6">Dossier Clients</h2>
            
            <div id="liste-clients-valides">
                <div class="text-center text-gray-500 py-8">Aucun client validé</div>
            </div>
        </div>

        <!-- Fiche Client Détaillée (pour affichage/impression) -->
        <div id="fiche-client-detail" class="hidden">
            <div class="no-print mb-4 text-center">
                <button onclick="window.print()" class="bg-green-600 text-white px-6 py-3 rounded-lg hover:bg-green-700 mr-4">
                    Imprimer
                </button>
                <button onclick="montrerSection('clients')" class="bg-gray-600 text-white px-6 py-3 rounded-lg hover:bg-gray-700">
                    Retour aux Clients
                </button>
            </div>
            <div class="print-area bg-white rounded-lg shadow-lg p-8" id="contenu-fiche-detail">
            </div>
        </div>

    </div>

    <script>
        let materiaux = [];
        let clientsValides = [];

        // Charger les clients sauvegardés
        document.addEventListener('DOMContentLoaded', function() {
            document.getElementById('date').value = new Date().toISOString().split('T')[0];
            chargerClients();
        });

        // Navigation entre sections
        function montrerSection(section) {
            // Cacher toutes les sections
            document.getElementById('section-saisie').classList.add('hidden');
            document.getElementById('section-clients').classList.add('hidden');
            document.getElementById('fiche-client-detail').classList.add('hidden');
            
            // Afficher la section demandée
            document.getElementById('section-' + section).classList.remove('hidden');
            
            // Mettre à jour les boutons
            document.querySelectorAll('button[id^="btn-"]').forEach(btn => {
                btn.className = 'px-4 py-3 bg-gray-300 rounded-t';
            });
            document.getElementById('btn-' + section).className = 'px-4 py-3 bg-green-600 text-white rounded-t';
        }

        // Ouvrir/fermer formulaire
        function ouvrir(id) {
            // Fermer tous les autres
            const tousFormulaires = [
                'autre-materiau',
                'terrasse-pin', 'terrasse-exotique', 'terrasse-ceramique',
                'allee-grouet', 'allee-aplite', 'gravier-030',
                'bordure-acier', 'bordure-pave',
                'arbres', 'gazon',
                'parpaing', 'couvertine', 'enduit'
            ];
            
            tousFormulaires.forEach(formId => {
                if (formId !== id) {
                    const form = document.getElementById(formId);
                    if (form) form.classList.add('hidden');
                }
            });
            
            // Ouvrir/fermer celui demandé
            const div = document.getElementById(id);
            if (div) {
                div.classList.toggle('hidden');
            }
        }

        // Ajouter matériau personnalisé
        function ajouterAutre(id) {
            const div = document.getElementById(id);
            if (!div) {
                alert('Erreur: formulaire non trouvé');
                return;
            }
            
            const inputs = div.querySelectorAll('input, select, textarea');
            if (inputs.length < 4) {
                alert('Erreur: champs manquants');
                return;
            }
            
            const nom = inputs[0].value.trim();
            const quantite = parseFloat(inputs[1].value);
            const unite = inputs[2].value;
            const notes = inputs[3].value;
            
            if (!nom) {
                alert('Veuillez saisir le nom du matériau');
                return;
            }
            
            if (!quantite || quantite <= 0) {
                alert('Veuillez saisir une quantité valide');
                return;
            }
            
            // Supprimer ancien si existe
            materiaux = materiaux.filter(m => m.nom !== nom);
            
            // Ajouter nouveau
            materiaux.push({
                nom: nom,
                quantite: quantite,
                unite: unite,
                notes: notes
            });
            
            afficher();
            
            // Fermer et vider
            div.classList.add('hidden');
            inputs[0].value = '';
            inputs[1].value = '';
            inputs[3].value = '';
            
            alert(`${nom} ajouté : ${quantite} ${unite}`);
        }

        // Ajouter matériau
        function ajouter(nom, id) {
            const div = document.getElementById(id);
            if (!div) {
                alert('Erreur: formulaire non trouvé');
                return;
            }
            
            const inputs = div.querySelectorAll('input, select, textarea');
            if (inputs.length < 3) {
                alert('Erreur: champs manquants');
                return;
            }
            
            const quantite = parseFloat(inputs[0].value);
            const unite = inputs[1].value;
            const notes = inputs[2].value;
            
            if (!quantite || quantite <= 0) {
                alert('Veuillez saisir une quantité valide');
                return;
            }
            
            // Supprimer ancien si existe
            materiaux = materiaux.filter(m => m.nom !== nom);
            
            // Ajouter nouveau
            materiaux.push({
                nom: nom,
                quantite: quantite,
                unite: unite,
                notes: notes
            });
            
            afficher();
            
            // Fermer et vider
            div.classList.add('hidden');
            inputs[0].value = '';
            inputs[2].value = '';
            
            alert(`${nom} ajouté : ${quantite} ${unite}`);
        }

        // Afficher liste
        function afficher() {
            const div = document.getElementById('liste-materiaux');
            
            if (materiaux.length === 0) {
                div.innerHTML = '<p class="text-gray-500 text-center py-4">Aucun matériau ajouté</p>';
                return;
            }
            
            let html = '';
            materiaux.forEach((m, i) => {
                html += `
                    <div class="border rounded p-3 mb-2 flex justify-between items-center">
                        <div>
                            <strong>${m.nom}</strong><br>
                            <span class="text-gray-600">${m.quantite} ${m.unite}</span>
                            ${m.notes ? '<br><small class="text-gray-500">' + m.notes + '</small>' : ''}
                        </div>
                        <button onclick="supprimer(${i})" class="bg-red-500 text-white px-3 py-1 rounded hover:bg-red-600">
                            Supprimer
                        </button>
                    </div>
                `;
            });
            div.innerHTML = html;
        }

        // Supprimer
        function supprimer(index) {
            materiaux.splice(index, 1);
            afficher();
        }

        // Valider et sauvegarder dans le dossier clients
        function valider() {
            const nom = document.getElementById('nom').value.trim();
            if (!nom) {
                alert('Le nom du client est obligatoire');
                return;
            }
            if (materiaux.length === 0) {
                alert('Veuillez ajouter au moins un matériau');
                return;
            }
            
            const client = {
                id: Date.now(),
                nom: nom,
                telephone: document.getElementById('telephone').value,
                email: document.getElementById('email').value,
                adresse: document.getElementById('adresse').value,
                date: document.getElementById('date').value,
                materiaux: [...materiaux],
                dateCreation: new Date().toLocaleString('fr-FR')
            };
            
            // Ajouter au dossier clients
            clientsValides.push(client);
            sauvegarderClients();
            
            alert(`Client ${nom} ajouté au dossier avec succès !`);
            
            // Réinitialiser le formulaire
            nouveau();
            
            // Aller au dossier clients
            montrerSection('clients');
            afficherClients();
        }

        // Sauvegarder les clients dans le navigateur
        function sauvegarderClients() {
            try {
                localStorage.setItem('albizia_clients_valides', JSON.stringify(clientsValides));
            } catch (e) {
                console.error('Erreur sauvegarde:', e);
            }
        }

        // Charger les clients sauvegardés
        function chargerClients() {
            try {
                const clients = localStorage.getItem('albizia_clients_valides');
                if (clients) {
                    clientsValides = JSON.parse(clients);
                    afficherClients();
                }
            } catch (e) {
                console.error('Erreur chargement:', e);
            }
        }

        // Afficher la liste des clients validés
        function afficherClients() {
            const div = document.getElementById('liste-clients-valides');
            
            if (clientsValides.length === 0) {
                div.innerHTML = '<div class="text-center text-gray-500 py-8">Aucun client validé</div>';
                return;
            }
            
            let html = '<div class="grid gap-4">';
            clientsValides.forEach(client => {
                html += `
                    <div class="bg-white rounded-lg shadow-lg p-4 border">
                        <div class="flex justify-between items-start">
                            <div class="flex-1">
                                <h3 class="font-bold text-lg text-green-800">${client.nom}</h3>
                                <div class="text-sm text-gray-600 mt-1">
                                    <p>Date: ${client.date}</p>
                                    ${client.telephone ? `<p>Tél: ${client.telephone}</p>` : ''}
                                    ${client.email ? `<p>Email: ${client.email}</p>` : ''}
                                </div>
                                <div class="mt-2">
                                    <span class="bg-blue-100 text-blue-800 px-2 py-1 rounded text-sm">
                                        ${client.materiaux.length} matériaux
                                    </span>
                                </div>
                                <p class="text-xs text-gray-500 mt-2">Créé le ${client.dateCreation}</p>
                            </div>
                            <div class="flex gap-2">
                                <button onclick="voirClient(${client.id})" class="bg-blue-600 text-white px-3 py-1 rounded text-sm hover:bg-blue-700">
                                    Voir
                                </button>
                                <button onclick="supprimerClient(${client.id})" class="bg-red-600 text-white px-3 py-1 rounded text-sm hover:bg-red-700">
                                    Suppr.
                                </button>
                            </div>
                        </div>
                    </div>
                `;
            });
            html += '</div>';
            div.innerHTML = html;
        }

        // Voir le détail d'un client
        function voirClient(id) {
            const client = clientsValides.find(c => c.id === id);
            if (!client) return;
            
            let html = `
                <div class="text-center mb-6">
                    <h1 class="text-3xl font-bold text-green-800">FICHE CLIENT</h1>
                    <p class="text-gray-600">Albizia Paysages</p>
                </div>
                
                <div class="mb-6 p-4 border rounded bg-gray-50">
                    <h2 class="text-xl font-bold mb-3">Informations Client</h2>
                    <div class="grid md:grid-cols-2 gap-4">
                        <div><strong>Nom:</strong> ${client.nom}</div>
                        <div><strong>Date:</strong> ${client.date}</div>
                        <div><strong>Téléphone:</strong> ${client.telephone || 'Non renseigné'}</div>
                        <div><strong>Email:</strong> ${client.email || 'Non renseigné'}</div>
                    </div>
                    ${client.adresse ? '<div class="mt-2"><strong>Adresse:</strong> ' + client.adresse + '</div>' : ''}
                </div>
                
                <div>
                    <h2 class="text-xl font-bold mb-4">Matériaux</h2>
                    <table class="w-full border">
                        <thead>
                            <tr class="bg-gray-100">
                                <th class="border p-3 text-left">Matériau</th>
                                <th class="border p-3 text-left">Quantité</th>
                                <th class="border p-3 text-left">Unité</th>
                                <th class="border p-3 text-left">Notes</th>
                            </tr>
                        </thead>
                        <tbody>
            `;
            
            client.materiaux.forEach(m => {
                html += `
                    <tr>
                        <td class="border p-3">${m.nom}</td>
                        <td class="border p-3">${m.quantite}</td>
                        <td class="border p-3">${m.unite}</td>
                        <td class="border p-3">${m.notes || '-'}</td>
                    </tr>
                `;
            });
            
            html += `
                        </tbody>
                    </table>
                </div>
                
                <div class="mt-6 text-center text-sm text-gray-500">
                    Client enregistré le ${client.dateCreation}
                </div>
            `;
            
            document.getElementById('contenu-fiche-detail').innerHTML = html;
            document.getElementById('fiche-client-detail').classList.remove('hidden');
            document.getElementById('section-clients').classList.add('hidden');
        }

        // Supprimer un client
        function supprimerClient(id) {
            if (confirm('Supprimer définitivement ce client ?')) {
                clientsValides = clientsValides.filter(c => c.id !== id);
                sauvegarderClients();
                afficherClients();
            }
        }

        // Nouveau
        function nouveau() {
            if (confirm('Nouveau dossier ? Les données actuelles seront perdues.')) {
                document.getElementById('nom').value = '';
                document.getElementById('telephone').value = '';
                document.getElementById('email').value = '';
                document.getElementById('adresse').value = '';
                document.getElementById('date').value = new Date().toISOString().split('T')[0];
                materiaux = [];
                afficher();
                document.getElementById('dossier-final').classList.add('hidden');
                window.scrollTo(0, 0);
            }
        }
    </script>
</body>
</html>
