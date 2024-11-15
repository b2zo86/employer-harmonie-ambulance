<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Harmonie Ambulance - Gestion des Employés</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        header {
            background-color: #0066cc;
            color: white;
            text-align: center;
            padding: 1em;
        }
        main {
            padding: 20px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }
        th, td {
            padding: 8px 12px;
            border: 1px solid #ddd;
        }
        th {
            background-color: #f2f2f2;
        }
        .form-container {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .form-container input {
            padding: 8px;
            margin: 5px;
            border-radius: 4px;
            border: 1px solid #ddd;
            width: 100%;
        }
        .form-container button {
            background-color: #28a745;
            color: white;
            border: none;
            padding: 10px 20px;
            cursor: pointer;
            width: 100%;
            margin-top: 10px;
        }
        .form-container button:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>

<header>
    <h1>Harmonie Ambulance - Gestion des Employés</h1>
</header>

<main>
    <div class="form-container">
        <h2>Ajouter un nouvel employé</h2>
        <form id="addEmployeeForm">
            <input type="text" id="employeeName" placeholder="Nom de l'employé" required>
            <input type="text" id="employeeId" placeholder="Identifiant" required>
            <input type="text" id="employeeSoftware" placeholder="Logiciels utilisés" required>
            <input type="text" id="employeeStatus" placeholder="Statut (actif/inactif)" required>
            <button type="submit">Ajouter Employé</button>
        </form>
    </div>

    <h2>Liste des Employés</h2>
    <table id="employeeTable">
        <thead>
            <tr>
                <th>Nom</th>
                <th>Identifiant</th>
                <th>Logiciels</th>
                <th>Statut</th>
                <th>Action</th>
            </tr>
        </thead>
        <tbody>
            <!-- Les employés seront ajoutés ici via JavaScript -->
        </tbody>
    </table>
</main>

<script>
    const addEmployeeForm = document.getElementById('addEmployeeForm');
    const employeeTable = document.getElementById('employeeTable').getElementsByTagName('tbody')[0];

    // Fonction pour ajouter un employé à la table
    function addEmployeeToTable(name, id, software, status) {
        const row = employeeTable.insertRow();

        const cell1 = row.insertCell(0);
        cell1.textContent = name;

        const cell2 = row.insertCell(1);
        cell2.textContent = id;

        const cell3 = row.insertCell(2);
        cell3.textContent = software;

        const cell4 = row.insertCell(3);
        cell4.textContent = status;

        const cell5 = row.insertCell(4);
        const deleteButton = document.createElement('button');
        deleteButton.textContent = 'Supprimer';
        deleteButton.onclick = () => row.remove(); // Suppression de l'employé
        cell5.appendChild(deleteButton);
    }

    // Écouter le formulaire pour ajouter un nouvel employé
    addEmployeeForm.addEventListener('submit', function(event) {
        event.preventDefault();

        const name = document.getElementById('employeeName').value;
        const id = document.getElementById('employeeId').value;
        const software = document.getElementById('employeeSoftware').value;
        const status = document.getElementById('employeeStatus').value;

        // Ajouter l'employé à la table
        addEmployeeToTable(name, id, software, status);

        // Réinitialiser le formulaire
        addEmployeeForm.reset();
    });
</script>

</body>
</html>
