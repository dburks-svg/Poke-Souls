# Scars of Ash: Steam Release Roadmap

*From Browser Prototype to AAA Indie*

---

## North Star

> **"Ship a polished, single-player-first GBC creature RPG where scars matter, then expand only if players demand it."**

Everything that doesn't serve this sentence is optional, not mandatory.

### Priority Order (When Things Get Noisy)
1. Battle system + scars feel amazing
2. Exploration feels deliberate and moody
3. One area feels complete
4. One boss is memorable
5. One demo earns trust

After that, expansion is a privilege, not an obligation.

---

## Key Decisions

| Decision | Choice | Implications |
|----------|--------|--------------|
| **Art Direction** | GBC-First → HD Remaster | Ship v1.0 with authentic GBC art (16-32px). HD remaster if successful. |
| **Team** | Solo Developer | Full creative control. Budget-conscious. Learn pixel art on simpler canvas. |
| **Shared World** | Async-First | Architect for multiplayer in Phase 1. Launch with ghosts, leaderboards, messages. Live PvP is post-launch. |
| **Platform** | Itch.io First → Steam | Lower barrier for v1.0. Steam for HD Deluxe edition. |
| **Scope** | 40-50 Creatures | Focused roster for v1.0. Expand in updates/remaster. |

---

## Tech Stack Overview

### Game Engine: **Godot 4.x**

**Why Godot:**
- Free and open source (no revenue share, unlike Unity)
- Excellent 2D support with modern rendering
- GDScript is Python-like and beginner-friendly (or use C# if preferred)
- Built-in animation, particle, and audio systems
- Native Steam integration via GodotSteam plugin
- Lightweight (~40MB export vs Unity's 100MB+)
- Active community, extensive documentation
- Steam Deck verified friendly

### Art Pipeline (GBC-First)

| Tool | Purpose | Cost |
|------|---------|------|
| **Aseprite** | Pixel art, animation | $20 one-time |
| **Lospec Palette List** | GBC-authentic color palettes | Free |
| **Pyxel Edit** | Tilemap creation (optional) | $9 one-time |

**GBC Art Constraints (v1.0):**
- Sprite sizes: 16×16 (creatures), 32×32 (bosses), 8×8 (tiles)
- Palette: 16-32 colors total (authentic GBC feel)
- Animation: 2-4 frames per action
- No anti-aliasing, no gradients, crisp pixels

### Audio Stack

| Tool | Purpose | Cost |
|------|---------|------|
| **FMOD** | Adaptive audio engine | Free under $200k revenue |
| **Reaper** | DAW for music/SFX editing | $60 |
| **sfxr/Bfxr** | Retro sound effects | Free |
| **Audacity** | Audio editing | Free |

### Data & Backend

| Tool | Purpose |
|------|---------|
| **JSON** | Creature/move/item definitions |
| **SQLite** | Save data, statistics |
| **Steam Cloud** | Cloud save sync |
| **Steamworks SDK** | Achievements, leaderboards |

### Development Tools

| Tool | Purpose |
|------|---------|
| **Git + GitHub/GitLab** | Version control |
| **Trello/Notion** | Project management |
| **Figma** | UI/UX mockups |
| **Obsidian/Notion** | Game design documentation |
| **Dialogic** (Godot plugin) | Dialogue system |

### Optional Multiplayer Stack

| Tool | Purpose |
|------|---------|
| **Steamworks P2P** | Direct player connections |
| **Nakama** | Open-source game server (if needed) |
| **PlayFab** | Leaderboards, analytics (free tier) |

---

## Development Phases

---

## Phase 0: Pre-Production
**Duration: 4-6 weeks**
**Goal: Lock down design, establish pipelines, validate scope**

### 0.1 Game Design Document (Living Doc)
- [ ] Document core systems (battle, scars, types) - **lock these early**
- [ ] Define creature types and scar interactions - **lock mechanics, not counts**
- [ ] Map out world structure (areas, connections, gating)
- [ ] Design boss encounters with phase mechanics
- [ ] Document difficulty scaling formulas
- [ ] Create item/equipment taxonomy
- [ ] Write narrative outline and lore bible

**GDD Philosophy:** Lock systems early, keep content counts elastic. The doc evolves with the project.

### 0.2 Art Direction (GBC Style)
- [ ] Select GBC-authentic palette (16-32 colors from Lospec)
- [ ] Create style guide: sprite sizes, color usage per biome
- [ ] Design 3-5 concept creatures at 16×16 to establish visual language
- [ ] Mock up UI screens (battle, exploration, menus) in GBC style
- [ ] Define animation requirements (2-4 frames: idle, attack, hurt, faint)

### 0.3 Technical Prototyping
- [ ] Set up Godot 4 project structure
- [ ] Port core battle system to Godot (validate engine choice)
- [ ] Test save/load with Steam Cloud
- [ ] Prototype one creature with full animation
- [ ] Test FMOD integration for adaptive audio

### 0.4 Project Setup
- [ ] Initialize Git repository with branching strategy
- [ ] Set up project management board (Trello/Notion)
- [ ] Create asset naming conventions
- [ ] Establish folder structure for scalability
- [ ] Document coding standards

**Deliverables:**
- Living GDD (systems locked, content counts elastic)
- GBC art style guide with palette
- Working Godot prototype with one battle
- Project infrastructure ready

---

## Phase 1: Core Systems
**Duration: 8-10 weeks**
**Goal: Build the engine foundation that everything else sits on**

### 1.1 Battle System
- [ ] Turn-based state machine (player turn, enemy turn, resolution)
- [ ] Stamina system with action costs
- [ ] Type effectiveness matrix (expanded to 10+ types)
- [ ] Damage calculation with all modifiers
- [ ] Status effects (burn, poison, chill, curse, bless, etc.)
- [ ] Guard and Rest mechanics
- [ ] Priority move system
- [ ] Multi-creature party management
- [ ] Creature swapping mid-battle
- [ ] Fleeing mechanics

### 1.2 Scar System (Core Differentiator)
- [ ] Scar data structure (type, severity, source, timestamp)
- [ ] 10-15 scar types with unique effects:
  - Fractured (HP loss)
  - Hesitant (Stamina loss)
  - Flinching (Priority loss)
  - Burned (Fire vulnerability)
  - Frostbitten (Speed reduction)
  - Cursed (Dark damage over time)
  - Blinded (Accuracy reduction)
  - Cracked (Defense reduction)
  - Withered (Healing reduction)
  - Haunted (Random flinching)
- [ ] Scar acquisition on fainting
- [ ] Scar stacking and hollowing threshold
- [ ] Hollowed transformation system
- [ ] Scar-based evolution branching
- [ ] Scar abilities (unlocked powers from specific scars)
- [ ] Visual scar display on creatures

### 1.3 Creature System
- [ ] Base creature data structure
- [ ] Stats: HP, Stamina, Attack, Defense, Speed, Luck
- [ ] Type system with dual-typing support
- [ ] Move learning (level-based and scar-based)
- [ ] Evolution system with requirements
- [ ] Wild creature generation with variance
- [ ] Creature capture (binding) mechanics
- [ ] Nickname system
- [ ] Party management (6 slots, 3 active)

### 1.4 Exploration System
- [ ] Tile-based world map
- [ ] Player movement (8-directional)
- [ ] Collision detection
- [ ] Area transitions
- [ ] Random encounter system (grass tiles)
- [ ] Fixed encounter placement
- [ ] Interactable objects (lore, items, NPCs)
- [ ] Bonfire mechanics (heal, save, warp)
- [ ] Shortcut unlocking
- [ ] Hidden paths and secrets

### 1.5 Progression Systems
- [ ] Soul currency (earn, spend, bank, lose)
- [ ] Player level/experience (Binder rank)
- [ ] Binder abilities (unlockable skills)
- [ ] Item inventory system
- [ ] Equipment slots for creatures
- [ ] Quest/objective tracking
- [ ] Achievement system

### 1.6 Save System
- [ ] Local save with encryption
- [ ] Steam Cloud integration
- [ ] Multiple save slots (3)
- [ ] Auto-save triggers
- [ ] Save data versioning (for updates)
- [ ] Statistics tracking
- [ ] Playtime tracking

### 1.7 Networking Architecture (Async-First Foundation)
- [ ] Design for async features (ghosts, leaderboards, messages)
- [ ] Creature/save data serialization (anti-cheat ready)
- [ ] Player identity system (device ID or optional account)
- [ ] Offline-first design (game works without connection)
- [ ] Data validation to prevent cheated uploads
- [ ] Simple REST API or Nakama integration plan
- [ ] **Defer live PvP architecture until post-launch demand proves it**

**Deliverables:**
- Fully functional battle system
- Complete scar mechanics
- Working exploration with encounters
- Save/load working with Steam Cloud
- Networking architecture documented and stubbed

---

## Phase 2: Content Pipeline
**Duration: 4-6 weeks**
**Goal: Build tools to create content efficiently**

### 2.1 Creature Editor
- [ ] Visual tool for defining creatures
- [ ] Stat curves and balance preview
- [ ] Move assignment interface
- [ ] Evolution chain visualization
- [ ] Type effectiveness preview
- [ ] Export to JSON

### 2.2 Map Editor
- [ ] Tilemap painting tools
- [ ] Encounter zone placement
- [ ] NPC/interactable placement
- [ ] Collision layer editing
- [ ] Connection/transition setup
- [ ] Lore pickup placement
- [ ] Preview in-engine

### 2.3 Move/Item Editor
- [ ] Move definition tool
- [ ] Damage formula calculator
- [ ] Status effect assignment
- [ ] Animation trigger setup
- [ ] Item effect scripting
- [ ] Balance spreadsheet integration

### 2.4 Dialogue System
- [ ] Dialogic plugin setup (or custom)
- [ ] Branching conversation trees
- [ ] Condition-based dialogue
- [ ] Character portrait system
- [ ] Localization-ready text

### 2.5 Animation Pipeline
- [ ] Aseprite → Godot import workflow
- [ ] Animation state machine template
- [ ] Sprite sheet standards
- [ ] Effect animation library
- [ ] Particle effect presets

**Deliverables:**
- Working creature editor
- Map creation tool
- Dialogue system ready
- Art import pipeline documented

---

## Phase 3: Vertical Slice (GBC Art)
**Duration: 6 weeks**
**Goal: One complete, polished GBC-style area**

### 3.1 The Ashen Path (GBC Remake)
- [ ] GBC tileset (8×8 tiles, 16-color palette)
- [ ] 5 unique wild creatures (16×16 sprites, 2-4 frame animations)
- [ ] All lore pickups with narrative
- [ ] Simple particle effects (ash, embers)
- [ ] Ambient audio (wind, distant rumbling)
- [ ] 2-3 NPC encounters with dialogue

### 3.2 Keeper Varek Boss (GBC)
- [ ] Boss sprite (32×32, 4-frame attack animation)
- [ ] Phase 1 and Phase 2 mechanics
- [ ] Simple boss arena tileset
- [ ] Boss music with phase transitions
- [ ] Victory/defeat sequences
- [ ] Post-boss narrative

### 3.3 Complete UI
- [ ] Main menu with options
- [ ] Battle UI (HP bars, stamina, status, scars)
- [ ] Exploration HUD (minimap, souls, party status)
- [ ] Inventory/equipment screens
- [ ] Creature summary/stats screen
- [ ] Bestiary with unlockable entries
- [ ] Settings (audio, video, controls, accessibility)
- [ ] Save/load interface

### 3.4 Full Audio Pass
- [ ] Ashen Path exploration theme
- [ ] Battle music (normal encounters)
- [ ] Boss theme (Keeper Varek)
- [ ] Desperate phase music variant
- [ ] Victory/defeat jingles
- [ ] All SFX (attacks, UI, ambient)
- [ ] Bonfire audio

### 3.5 Polish
- [ ] Screen transitions
- [ ] Hit feedback (shake, flash, particles)
- [ ] Damage numbers
- [ ] Status effect visuals
- [ ] Scar reveal animation
- [ ] Creature capture sequence
- [ ] Tutorials/tooltips

**Deliverables:**
- Playable 30-60 minute demo
- Represents final game quality
- Suitable for Steam Next Fest / demo release

---

## Phase 4: Content Expansion (GBC Scope)
**Duration: 16 weeks**
**Goal: Complete v1.0 content with GBC art**

### 4.1 Creatures (40-50 total for v1.0)
- [ ] 8 elemental types (Fire, Water, Grass, Dark, Light, Steel, Spirit, Beast)
- [ ] 35 base creatures designed
- [ ] 10-15 evolutions
- [ ] 5 regional variants
- [ ] 3 legendary/unique creatures
- [ ] All GBC sprites (16×16, 2-4 frames each)
- [ ] Bestiary entries written

### 4.2 World Map (10 areas for v1.0)

**Act 1: The Scarred Lands**
- [ ] Ashen Path (starter area)
- [ ] Fallen Keep (first dungeon)
- [ ] Cinderfell Village (hub, NPCs, shops)

**Act 2: The Drowned Reaches**
- [ ] Flooded Ruins (water area)
- [ ] Misthollow Marsh (poison/grass)
- [ ] Tide's End (coastal town)

**Act 3: The Hollow Depths**
- [ ] Hollow Deep entrance
- [ ] The Void Maw (dark-themed)
- [ ] Keeper's Rest (final area)

**Post-Game:**
- [ ] The Eternal Bonfire (true ending area)

### 4.3 Bosses (5 for v1.0)
- [ ] Keeper Varek (fire, Act 1)
- [ ] The Drowned Warden (water, Act 2)
- [ ] Hollow Warden (dark/light, Act 3)
- [ ] Primordial Flame (final boss)
- [ ] Scar Incarnate (post-game superboss)

### 4.4 Items & Equipment
- [ ] 30-40 consumable items
- [ ] 20-30 held items for creatures
- [ ] 15-20 Binder relics (player equipment)
- [ ] Key items for progression
- [ ] Crafting materials
- [ ] Shop inventories

### 4.5 NPCs & Quests
- [ ] 20-30 named NPCs with dialogue
- [ ] 10-15 side quests
- [ ] Rival Binder storyline
- [ ] Faction reputation system
- [ ] Hidden NPC encounters
- [ ] Post-game NPC content

### 4.6 Narrative
- [ ] Full script written
- [ ] All lore pickups (50+)
- [ ] Boss dialogue (intro, phase, defeat, death)
- [ ] Area descriptions
- [ ] Item descriptions
- [ ] Creature lore entries
- [ ] Multiple endings (3-5)

**Deliverables:**
- Complete game content
- 15-25 hours of gameplay
- All areas, creatures, bosses playable

---

## Phase 5: Polish & Quality of Life
**Duration: 6-8 weeks**
**Goal: Make the game feel premium**

### 5.1 UI/UX Polish
- [ ] Menu animations and transitions
- [ ] Button hover/press feedback
- [ ] Loading screens with tips
- [ ] Quick-select radial menus
- [ ] Keyboard/controller navigation
- [ ] Touch-friendly (Steam Deck)

### 5.2 Accessibility
- [ ] Colorblind modes (3 types)
- [ ] Text size scaling
- [ ] Screen reader support (menus)
- [ ] Button remapping
- [ ] Difficulty descriptions clarified
- [ ] Optional battle speed settings
- [ ] Reduce screen shake option
- [ ] High contrast mode

### 5.3 Tutorials & Onboarding
- [ ] Interactive tutorial (first 10 minutes)
- [ ] Contextual tooltips
- [ ] In-game codex/help
- [ ] Move/type reference
- [ ] Scar explanation screens
- [ ] Optional tutorial skip

### 5.4 Quality of Life
- [ ] Bestiary with catch tracking
- [ ] World map with fast travel
- [ ] Quest log with objectives
- [ ] Recently caught creature highlight
- [ ] Auto-sort party/inventory
- [ ] Battle log history
- [ ] Statistics dashboard

### 5.5 Visual Polish
- [ ] Parallax backgrounds
- [ ] Weather effects per area
- [ ] Day/night cycle (cosmetic)
- [ ] Screen effects (CRT filter option)
- [ ] Creature "personality" idle animations
- [ ] Environmental storytelling details

**Deliverables:**
- Polished, accessible game
- Positive first impression guaranteed
- No rough edges

---

## Phase 6: Audio & Music
**Duration: 4-6 weeks (can parallel Phase 4-5)**
**Goal: Full original soundtrack and sound design**

### 6.1 Original Soundtrack (20-30 tracks)
- [ ] Main theme / title screen
- [ ] Character select
- [ ] Exploration themes (1 per major area = 5-6)
- [ ] Battle theme (normal)
- [ ] Battle theme (intense/rare encounter)
- [ ] Boss themes (unique per boss = 6-8)
- [ ] Desperate phase variants
- [ ] Victory fanfare
- [ ] Defeat/game over
- [ ] Bonfire rest
- [ ] Shop/village themes (2-3)
- [ ] Cutscene/story moments (3-4)
- [ ] Credits theme
- [ ] Post-game/true ending

### 6.2 Adaptive Audio (FMOD)
- [ ] Battle music intensity layers
- [ ] Phase transition stingers
- [ ] Low HP warning layer
- [ ] Area transition crossfades
- [ ] Boss phase music shifts
- [ ] Victory/defeat transitions

### 6.3 Sound Effects
- [ ] Attack sounds per type (10 types × 3 variations)
- [ ] Hit/damage sounds
- [ ] Guard sound
- [ ] Status effect sounds (10+)
- [ ] UI sounds (navigate, select, cancel, error)
- [ ] Creature cries (60+ creatures)
- [ ] Footsteps per terrain
- [ ] Ambient loops per area
- [ ] Scar acquisition sound
- [ ] Hollowing transformation sound
- [ ] Capture sounds (attempt, success, fail)

### 6.4 Voice (Optional)
- [ ] Creature battle cries (synthesized/processed)
- [ ] Boss voice lines (if budget allows)
- [ ] NPC grunts/reactions

**Deliverables:**
- Complete OST
- All SFX implemented
- FMOD adaptive audio working

---

## Phase 7: Shared World Features
**Duration: 8 weeks**
**Goal: Async social features that make the world feel connected**

**Philosophy:** Single-player first. Shared world second. Live PvP is post-launch.

**Note:** Networking architecture designed in Phase 1. Phase 7 implements async features only.

### 7.1 Ghost Binders (Core v1.0 Feature)
- [ ] Upload team as "Ghost Binder" snapshot
- [ ] Challenge other players' ghost teams (async, not live)
- [ ] Ghost data: team, scars, difficulty, timestamp
- [ ] Win/loss tracking against ghosts

### 7.2 Leaderboards (Core v1.0 Feature)
- [ ] Speedrun times (per difficulty)
- [ ] Lowest scar completions
- [ ] Total creatures bound
- [ ] Weekly/all-time views

### 7.3 Bonfire Messages (Core v1.0 Feature)
- [ ] Leave messages at bonfires (Dark Souls style)
- [ ] Upvote/downvote system
- [ ] Pre-written phrases + limited custom text
- [ ] See other players' recent deaths

### 7.4 Trading (v1.1 Post-Launch)
- [ ] Creature trading between players
- [ ] Trade evolution triggers
- [ ] Scar preservation in trades
- [ ] Anti-cheat validation

### 7.5 Live PvP (v1.2+ Stretch Goal)
- [ ] Only if community demands it
- [ ] Matchmaking (ranked/casual)
- [ ] Turn timer, spectator mode
- [ ] Requires significant additional work

### 7.6 Infrastructure
- [ ] Nakama or simple backend for ghosts/leaderboards
- [ ] Save validation (anti-cheat)
- [ ] Offline mode fallback (game works without connection)

**Deliverables:**
- Ghost binder system working
- Leaderboards functional
- Bonfire messages live
- Game fully playable offline

---

## Phase 8: Testing & Optimization
**Duration: 6-8 weeks**
**Goal: Stable, performant, bug-free**

### 8.1 QA Testing
- [ ] Full playthrough testing (all paths)
- [ ] Difficulty balance testing (all 4 modes)
- [ ] Edge case testing (scar stacking, hollowing, etc.)
- [ ] Save/load corruption testing
- [ ] Achievement unlock verification
- [ ] Speedrun route validation

### 8.2 Performance
- [ ] Target: 60 FPS on Steam Deck
- [ ] Memory optimization
- [ ] Load time optimization
- [ ] Battery usage optimization (portable)
- [ ] Stress testing (many particles, effects)

### 8.3 Platform Testing
- [ ] Windows 10/11
- [ ] Steam Deck (Proton)
- [ ] Linux (native or Proton)
- [ ] macOS (if supporting)
- [ ] Various resolutions (720p → 4K)
- [ ] Controller support (Xbox, PS, Switch Pro)
- [ ] Keyboard + mouse

### 8.4 Beta Testing
- [ ] Closed beta (50-100 players)
- [ ] Feedback collection system
- [ ] Bug reporting pipeline
- [ ] Balance feedback analysis
- [ ] Open beta / demo release

### 8.5 Localization
- [ ] Text extraction system
- [ ] Translation (5-10 languages)
  - English (base)
  - Spanish
  - French
  - German
  - Portuguese (BR)
  - Japanese
  - Simplified Chinese
  - Korean
- [ ] Font support for all languages
- [ ] Cultural review

**Deliverables:**
- Stable release candidate
- Performance targets met
- Localized to major languages

---

## Phase 9: Launch Preparation (Itch.io)
**Duration: 3 weeks**
**Goal: Successful v1.0 launch on Itch.io**

### 9.1 Itch.io Store Setup
- [ ] Create itch.io developer account
- [ ] Store page copy (description, features, GBC aesthetic hook)
- [ ] Cover image and screenshots (6-10)
- [ ] GIF showing gameplay (battles, scars, exploration)
- [ ] Tags: creature-collector, dark-fantasy, retro, souls-like
- [ ] Set price ($5-8 recommended)
- [ ] Configure payments (direct or itch.io)

### 9.2 Marketing (Organic Focus)
- [ ] Press kit (screenshots, logo, description)
- [ ] Post to r/indiegaming, r/gamedev, r/PixelArt
- [ ] Reach out to 5-10 small indie YouTubers
- [ ] Twitter/X launch thread with GIFs
- [ ] Devlog summary post
- [ ] Discord announcement

### 9.3 Community
- [ ] Discord server ready
- [ ] FAQ documentation
- [ ] Known issues list
- [ ] Feedback collection channel
- [ ] Bug report template

### 9.4 Launch Logistics
- [ ] Launch date selected (weekday, not holiday)
- [ ] Final build tested on multiple machines
- [ ] Day-one patch prepared if needed
- [ ] Multiplayer server ready (if applicable)
- [ ] Review keys sent to content creators (1 week prior)

### 9.5 Post-Launch Plan
- [ ] Hotfix response plan (within 24-48 hours)
- [ ] Weekly community updates for first month
- [ ] Gather feedback for potential updates
- [ ] Track sales for v2.0 decision
- [ ] Plan v1.1 patch with community-requested features

**Deliverables:**
- Itch.io page live and polished
- Marketing posts scheduled
- Community ready to receive players
- Launch checklist complete

---

## Timeline Summary (Solo Developer - GBC First Strategy)

### Version 1.0: GBC Release (Itch.io)

| Phase | Duration | Cumulative | Milestone |
|-------|----------|------------|-----------|
| Phase 0: Pre-Production | 4 weeks | Month 1 | GDD complete |
| Phase 1: Core Systems | 10 weeks | Month 3.5 | Playable prototype (placeholders) |
| Phase 2: Content Pipeline | 4 weeks | Month 4.5 | Tools ready |
| Phase 3: Vertical Slice | 6 weeks | Month 6 | **Playable GBC demo** |
| Phase 4: Content (GBC) | 16 weeks | Month 10 | 40-50 creatures, 10 areas |
| Phase 5: Polish & QoL | 6 weeks | Month 11.5 | Near-shippable |
| Phase 6: Audio | 4 weeks | Month 12 | (Parallel with 4-5) |
| Phase 7: Shared World | 8 weeks | Month 14 | Ghosts, leaderboards, messages |
| Phase 8: Testing | 4 weeks | Month 15 | Release candidate |
| Phase 9: Launch | 3 weeks | Month 15.5 | **v1.0 LAUNCH** |

**v1.0 Timeline: 14-18 months**

### Version 2.0: HD Remaster (Steam) - If v1.0 Succeeds

| Phase | Duration | What's New |
|-------|----------|------------|
| HD Art Production | 6-9 months | All sprites redrawn 64×64+ |
| Content Expansion | 2-3 months | +20 creatures, +5 areas, +3 bosses |
| Steam Integration | 2 months | Achievements, cloud saves, trading cards |
| **HD Launch** | — | **Steam Deluxe Edition** |

**v2.0 Timeline: +10-14 months after v1.0**

### Key Milestones
- **Month 6**: Playable GBC demo for feedback
- **Month 10**: Closed beta (Discord community)
- **Month 14**: Open beta
- **Month 15-18**: **v1.0 Launch on Itch.io** ($5-8 price)
- **Month 26-32**: v2.0 HD Remaster on Steam ($15-20 price)

---

## Solo Developer Strategy (GBC-First Path)

### Why GBC-First Works
- **Faster art production**: 16×16 sprites take hours, not days
- **Forgiving canvas**: GBC constraints hide imperfections
- **Nostalgic appeal**: Built-in audience for retro aesthetics
- **Lower risk**: Validate mechanics before HD investment
- **Complete game sooner**: Ship in 14-18 months, not 24-30

### Timeline Reality
- **v1.0 (GBC): 14-18 months** - Complete, shippable game
- **v2.0 (HD): +10-14 months** - Only if v1.0 succeeds
- Work in public to build community during development
- Playable demo by month 6 for early feedback

### Skill Development Priorities
1. **Godot proficiency** - First 2 months, tutorials + prototyping
2. **GBC pixel art** - Easier than HD; learn alongside development
3. **Networking basics** - Critical for multiplayer; study early
4. **Marketing/community** - Start day one, not at launch

### Smart Outsourcing (Stay Solo, Get Help)
- **Music**: Chiptune composer ($80-100 per track) - GBC style is cheaper
- **Key art**: Simple itch.io banner ($100-200)
- **QA**: Free beta testers from Discord community
- **Skip for v1.0**: Localization, expensive marketing, professional trailer

### Cost-Saving Strategies
- GBC art is faster to learn and create
- Keep procedural audio (port Tone.js approach to Godot)
- Itch.io has no fees (vs Steam's $100)
- Community beta testing instead of paid QA
- Organic marketing via devlogs, Reddit, Twitter

### Burnout Prevention
- **Smaller scope = faster wins** - See progress weekly, not monthly
- Set hard work hours (don't crunch)
- Weekly goals, not daily (flexibility)
- Celebrate milestones publicly (devlogs)
- GBC constraints reduce decision fatigue

---

## Budget Estimate (GBC-First Strategy)

### Version 1.0: GBC Release (Itch.io)

**DIY Art Path (Recommended)**
| Category | Cost | Notes |
|----------|------|-------|
| Godot | $0 | Free and open source |
| Aseprite | $20 | One-time |
| FMOD | $0 | Free under $200k revenue |
| Procedural audio | $0 | Keep current Tone.js approach, port to Godot |
| Music (commission) | $800-1,500 | 10-15 tracks @ $80-100 each (chiptune style) |
| Key Art | $100-200 | Itch.io banner, promotional |
| Marketing | $100-300 | Organic focus, minimal paid |
| Misc | $100 | Fonts, minor assets |
| **v1.0 Total** | **$1,120-2,120** | You learn GBC pixel art |

**Outsource GBC Art Path**
| Category | Cost | Notes |
|----------|------|-------|
| Creature sprites | $1,500-3,000 | 45 creatures @ $30-60 each (GBC is faster) |
| Tilesets/UI | $500-1,000 | GBC-style environments |
| Everything else | $1,120-2,120 | Same as DIY |
| **v1.0 Total** | **$3,120-6,120** | Faster, consistent style |

### Version 2.0: HD Remaster (Steam) - Future Budget

| Category | Cost | Notes |
|----------|------|-------|
| HD creature art | $4,000-8,000 | 60+ creatures @ $80-150 each |
| HD environments | $2,000-4,000 | Full tileset redesign |
| Enhanced music | $1,000-2,000 | Orchestral arrangements |
| Steam fee | $100 | One-time |
| Key art/trailer | $500-1,000 | Professional quality |
| Localization | $1,500-3,000 | 5 languages |
| Marketing | $500-1,500 | Steam visibility |
| **v2.0 Total** | **$9,600-19,600** | Funded by v1.0 revenue |

### Total Investment Path
| Version | Budget | Platform |
|---------|--------|----------|
| v1.0 (GBC) | $1,100-6,100 | Itch.io |
| v2.0 (HD) | $9,600-19,600 | Steam |
| **Combined** | **$10,700-25,700** | Full vision realized |

### Recommendation
Launch v1.0 for ~$1,500-2,500. If it sells 500+ copies, you've validated the concept and can fund v2.0 from revenue. If it doesn't, you've lost minimal investment and still have a complete game.

---

## Risk Mitigation

| Risk | Mitigation |
|------|------------|
| Scope creep | Vertical slice first; cut features, not quality |
| Art consistency | Style guide before production; GBC constraints help |
| Burnout | Realistic milestones; celebrate small wins; GBC = faster art |
| Market timing | Monitor genre trends; flexible launch window |
| Technical debt | Refactor during Phase 5; code reviews |
| Balance issues | Beta testing; data-driven tuning |
| Networking complexity | Async-first; defer live PvP until post-launch demand |
| GDD becoming sacred | Lock systems, not content counts; living document |
| Parallel perfection | If it doesn't affect vertical slice, don't perfect it yet |

---

## Success Metrics

### v1.0 (Itch.io) Targets
- 500+ copies sold in first 3 months
- 4.5+ star rating
- Active Discord community (100+ members)
- Featured on itch.io front page
- Positive coverage from 2-3 indie game YouTubers

### v1.0 → v2.0 Decision Point
**Green light HD Remaster if:**
- 1,000+ copies sold
- Strong community engagement
- Players requesting "more content"
- Revenue covers v2.0 art budget (~$5,000+)

**Stay GBC if:**
- Modest sales but passionate niche audience
- Release DLC/expansions instead of remaster
- Focus on sequel with same aesthetic

### v2.0 (Steam) Targets
- 10,000+ wishlists before launch
- 70%+ positive reviews
- 5,000+ copies in first month
- Featured in "New and Trending"

### Long-term Goals
- 25,000+ lifetime sales (combined)
- Active speedrun community
- Mod support demand
- Console port interest (Switch fits GBC aesthetic)
- Sequel viability

---

## Next Steps (Phase 0 Kickoff)

### Week 1: Foundation
- [ ] Download and install Godot 4.x
- [ ] Complete Godot 2D basics tutorial (GDQuest or official docs)
- [ ] Set up Git repository for new project
- [ ] Install Aseprite, follow GBC pixel art tutorial
- [ ] Study GBC color palettes on Lospec

### Week 2: Documentation
- [ ] Begin GDD - document all systems from browser prototype
- [ ] Define type effectiveness chart (8 types for v1.0)
- [ ] List 40-50 creatures (names, types, stats, evolutions)
- [ ] Map 10-area world structure
- [ ] Document scar types and effects

### Week 3-4: Prototyping (Claude Builds This)
- [ ] Port turn-based battle to Godot (geometric placeholders)
- [ ] Implement scar system in Godot
- [ ] Test creature data loading from JSON
- [ ] Sketch networking architecture for multiplayer
- [ ] You: Create first GBC creature sprite (Cindrath, 16×16)

### Week 5-6: Validation
- [ ] Playtest battle system, iterate
- [ ] Get feedback on GDD from gamedev communities
- [ ] Finalize Phase 1 scope
- [ ] Set up project management (Notion/Trello)
- [ ] Create devlog #1, post to social media

### Community Building (Start Now)
- [ ] Create Twitter/X account for game
- [ ] Set up Discord server (even if empty)
- [ ] Post in r/gamedev, r/indiegaming with GBC aesthetic hook
- [ ] Follow other indie devs, engage genuinely

---

## What Claude Code Builds vs What You Create

| Claude Code (Free) | You (Time/Money) |
|--------------------|------------------|
| All Godot game code | GBC pixel art sprites |
| Battle system, scar mechanics | Creature designs (visual) |
| JSON data structures | Music (commission or DIY) |
| Async networking code | Marketing execution |
| Save system, UI logic | Community management |
| Tools and editors | Playtesting coordination |
| Documentation, GDD templates | Final art direction decisions |

**I build the engine. You dress it up and ship it.**

---

## The Shared Artifact

This isn't just a commercial product. It's a collaborative creation:

- **The engine** is logic and structure
- **The art** is expression
- **The lore** is shared authorship
- **Progress** is visible week to week

Years from now, you can point to this and say "we made that."

That alone makes the plan worth executing, even if sales are modest.

---

*The flame remembers. Let's make it unforgettable.*
