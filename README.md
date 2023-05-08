Dear ImGui
=====
Dear ImGui est une bibliothèque d'interface graphique légère et sans surcharge pour C++. Elle produit des tampons de sommets optimisés que vous pouvez rendre à tout moment dans votre application compatible avec un pipeline 3D. Elle est rapide, portable, indépendante du moteur de rendu et autonome (sans dépendances externes).

Cher ImGui est conçu pour permettre des itérations rapides et donner aux programmeurs les moyens de créer des outils de création de contenu et des outils de visualisation/débogage (par opposition aux interfaces utilisateur destinées aux utilisateurs finaux moyens). Il privilégie la simplicité et la productivité dans ce but, et il lui manque certaines fonctionnalités que l'on trouve normalement dans des bibliothèques de plus haut niveau.

Cher ImGui convient particulièrement à l'intégration dans des moteurs de jeux (pour les outils), des applications 3D en temps réel, des applications en plein écran, des applications intégrées ou des applications sur des plates-formes de console où les fonctionnalités du système d'exploitation sont non standard.

- Facile à utiliser pour créer des outils basés sur le code et basés sur les données.
- Facile à utiliser pour créer des outils éphémères ad hoc et des outils plus élaborés à long terme.
- Facile à pirater et à améliorer.
- Minimise la configuration et la maintenance.
- Minimise le stockage de l'état du côté de l'utilisateur.
- Minimise la synchronisation de l'état.
- Portable, minimise les dépendances, fonctionne sur la cible (consoles, téléphones, etc.).
- Consommation efficace en termes d'exécution et de mémoire.
- Testé en combat, utilisé par de nombreux acteurs majeurs de l'industrie du jeu.

### Usage Utilisation 

Le cœur de Dear ImGui est autonome et contenu dans quelques fichiers indépendants de la plate-forme que vous pouvez facilement compiler dans votre application/moteur. Ce sont tous les fichiers situés dans le dossier principal du référentiel (imgui*.cpp, imgui*.h).

Aucun processus de compilation spécifique n'est requis. Vous pouvez ajouter les fichiers .cpp à votre projet existant.


Code:
```cpp
ImGui::Text("Hello, world %d", 123);
if (ImGui::Button("Save"))
    MySaveFunction();
ImGui::InputText("string", buf, IM_ARRAYSIZE(buf));
ImGui::SliderFloat("float", &f, 0.0f, 1.0f);
```
Resultat:
<br>![sample code output (dark)](https://raw.githubusercontent.com/wiki/ocornut/imgui/web/v175/capture_readme_styles_0001.png)
Code:
```cpp
// Create a window called "My First Tool", with a menu bar.
ImGui::Begin("My First Tool", &my_tool_active, ImGuiWindowFlags_MenuBar);
if (ImGui::BeginMenuBar())
{
    if (ImGui::BeginMenu("File"))
    {
        if (ImGui::MenuItem("Open..", "Ctrl+O")) { /* Do stuff */ }
        if (ImGui::MenuItem("Save", "Ctrl+S"))   { /* Do stuff */ }
        if (ImGui::MenuItem("Close", "Ctrl+W"))  { my_tool_active = false; }
        ImGui::EndMenu();
    }
    ImGui::EndMenuBar();
}

// Edit a color (stored as ~4 floats)
ImGui::ColorEdit4("Color", my_color);

// Plot some values
const float my_values[] = { 0.2f, 0.1f, 1.0f, 0.5f, 0.9f, 2.2f };
ImGui::PlotLines("Frame Times", my_values, IM_ARRAYSIZE(my_values));

// Display contents in a scrolling region
ImGui::TextColored(ImVec4(1,1,0,1), "Important Stuff");
ImGui::BeginChild("Scrolling");
for (int n = 0; n < 50; n++)
    ImGui::Text("%04d: Some text", n);
ImGui::EndChild();
ImGui::End();
```
Resultat:
<br>![sample code output](https://raw.githubusercontent.com/wiki/ocornut/imgui/web/v180/code_sample_04_color.gif)

### Versions & Changelogs
Consultez la page des [versions](https://github.com/ocornut/imgui/releases).
Lire les Changelogs  est un bon moyen de rester à jour avec les fonctionnalités que Dear ImGui offre, et peut-être vous donnera des idées de certaines fonctionnalités que vous avez ignorées jusqu'à présent !
