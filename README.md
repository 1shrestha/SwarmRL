# SwarmRL
Short: SwarmRL is a multi-agent deep RL simulator where 50 drones learn to cooperatively search a disaster zone.
# SwarmRL: Multi-Agent Deep RL Drone Swarm Simulator

SwarmRL trains a swarm of **50 drones** to cooperatively search a disaster zone using **multi-agent reinforcement learning**. The drones learn coordination on their own, and you can watch training and behaviour live in a **3D web dashboard**.

## Highlights

- **50-drone swarm** searching a simulated disaster zone
- **MAPPO** (Multi-Agent PPO) trained with **Ray RLlib**
- **PyTorch actor-critic** networks
- **PettingZoo** multi-agent environment
- **Real-time 3D dashboard** built with React and Three.js
- **Python WebSocket server** streaming simulation state to the browser

## Architecture

```
┌───────────────────┐     ┌──────────────────────┐     ┌──────────────────────┐
│  PettingZoo Env   │ --> │  Ray RLlib (MAPPO)   │ --> │  WebSocket Server    │
│  (disaster zone,  │     │  PyTorch actor-critic│     │  (Python)            │
│   50 drones)      │ <-- │  training / inference│     └──────────┬───────────┘
└───────────────────┘     └──────────────────────┘                │ live state
                                                                  v
                                                     ┌──────────────────────┐
                                                     │ React + Three.js 3D  │
                                                     │ Dashboard            │
                                                     └──────────────────────┘
```

1. **Environment:** a PettingZoo environment models the disaster zone and the drones' observations, actions and rewards.
2. **Training:** Ray RLlib runs MAPPO, with a PyTorch actor-critic policy shared across the swarm.
3. **Streaming:** a Python WebSocket server pushes simulation state to connected clients.
4. **Visualization:** the React + Three.js dashboard renders the drones and the zone in 3D in real time.

## Tech Stack

| Layer | Technology |
|---|---|
| RL algorithm | MAPPO |
| Training framework | Ray RLlib |
| Models | PyTorch (actor-critic) |
| Environment | PettingZoo |
| Server | Python, WebSockets |
| Frontend | React, Three.js |

## Getting Started

### Prerequisites

- Python 3.10+
- Node.js 18+
- (Optional) GPU for faster training

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/swarmrl.git
cd swarmrl
```

### 2. Set up the Python backend

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Train the swarm

```bash
python train.py
```

### 4. Start the WebSocket server

```bash
python server.py
```

### 5. Run the dashboard

```bash
cd dashboard
npm install
npm run dev
```

Open the URL shown in the terminal (usually `http://localhost:3000` or `http://localhost:5173`) to watch the swarm.

> The script names and folders above are placeholders. Adjust them to match your actual repository.

## Suggested Project Structure

```
swarmrl/
├── env/              # PettingZoo environment (disaster zone, drones, rewards)
├── training/         # RLlib MAPPO configs and training scripts
├── models/           # PyTorch actor-critic networks
├── server/           # Python WebSocket server
├── dashboard/        # React + Three.js 3D frontend
├── docs/             # Report, diagrams, screenshots
├── requirements.txt
└── README.md
```

## Roadmap

The project follows a 4-week plan with a mid-project review and a final review.

- [ ] Week 1: environment design and drone dynamics
- [ ] Week 2: MAPPO training pipeline with RLlib (mid-project review)
- [ ] Week 3: WebSocket server and 3D dashboard integration
- [ ] Week 4: tuning, evaluation, documentation (final review)

## Team

| Name |
|---|
| Srikanth |
| Fareed |
| Naitik |
| Vanshika |
| Shrestha |
| Sowbarnika |
| Gowtham |

## License

Add a license of your choice (for example MIT) before publishing.

## Acknowledgements

- [Ray RLlib](https://docs.ray.io/en/latest/rllib/index.html)
- [PettingZoo](https://pettingzoo.farama.org/)
- [PyTorch](https://pytorch.org/)
- [Three.js](https://threejs.org/)
