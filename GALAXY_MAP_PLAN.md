# Implementation Plan: MAIS Galaxy Map

## 1. Objective
To create a high-fidelity, interactive 3D visualization that demonstrates the "Distributed Graph" nature of the Multi-Agency Information Sharing (MAIS) infrastructure. The map will serve as a powerful storytelling tool for stakeholders, showing how disparate data entities (Persons, Professionals, Services) connect across agency boundaries.

## 2. Technical Stack
- **Engine:** `3d-force-graph` (WebGL/Three.js based).
- **Data Format:** JSON-LD (Linked Data).
- **Frontend:** Single-page HTML/JavaScript (portable and browser-native).
- **Styling:** CSS-in-JS or a dedicated stylesheet for a "Cyber/Space" aesthetic.

## 3. Visual Metaphor: "The Social Care Constellation"
- **Background:** Deep space (dark grey/black with subtle starfield).
- **Nodes (Celestial Bodies):**
    - **Person (Planet):** Blue-glowing spheres. Size scales with the number of connections.
    - **Professional (Station):** Green-glowing octahedrons or diamonds.
    - **Service (Star):** Large, bright yellow/orange spheres. Professionals "orbit" these services.
    - **Events/Episodes (Comets):** Small, white/cyan points that sit on the edges between Persons and Professionals/Services.
- **Edges (Gravitational Links):**
    - **Active Links:** Solid glowing lines.
    - **Historical/Closed Links:** Dotted or faint lines.
    - **Directionality:** Moving "photons" or pulses that travel from Subject to Object.

## 4. Feature Requirements
- **Camera Controls:** Smooth zoom, pan, and rotate.
- **Fly-to Interaction:** Clicking a node centers the camera and highlights its immediate "constellation" (1st-degree neighbors) while dimming the rest of the galaxy.
- **Data Inspector:** A side panel that appears on hover/click, showing the JSON-LD properties (Names, Roles, Identifiers).
- **Search:** A simple UI to find a specific Person or Professional by name/ID and jump to them.
- **State Toggle:** A "Silo vs. Network" toggle:
    - **Silo Mode:** Nodes are clustered by agency/service with no cross-agency links.
    - **Network Mode:** Links between clusters light up, showing the impact of the MAIS standards.

## 5. Implementation Phases

### Phase 0: Prerequisites (Critical Path)
The Galaxy Map requires a valid Linked Data graph to function. The following must be completed first:
1. **JSON-LD Contexts:** Map all schema fields to URIs so the graph engine can resolve relationships.
2. **Taxonomy Completion:** Finalize the `RelationshipCode` and `RoleCode` lists in `/controlled-vocabularies`. The map uses these to determine the "Visual Geometry" of a node (e.g., GP vs. Social Worker).
3. **URI Policy:** Adopt a consistent URI pattern for entities so the engine can uniquely identify nodes across agency boundaries.

### Phase 1: Data Scaffolding
- Generate a validated sample graph of ~50-100 entities using the new Context and URIs.
- Ensure the sample data includes "Inverse Relationships" to test graph traversal.

### Phase 2: Engine Setup
- Boilerplate HTML with `3d-force-graph` import.
- Configure Three.js lighting and space environment.
- Map JSON-LD types to 3D geometries.

### Phase 3: Interaction & UI
- Implement the "Fly-to" logic.
- Build the overlay for node metadata.
- Add the "Silo/Network" transition animation.

### Phase 4: Refinement
- Fine-tune force-directed layout (ensure Persons are central to their care networks).
- Add glowing shaders and "pulse" effects for active data exchanges.
