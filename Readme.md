# Professional Casino & Slot Games Platform


### **Enterprise-Grade Gaming Solution for Modern Casinos**

[![Telegram](https://img.shields.io/badge/Telegram-Contact%20Us-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/igamezgamble)

**Real-Time Multiplayer • Scalable Architecture • Production-Ready**

[![Laravel](https://img.shields.io/badge/Laravel-10.x-FF2D20?style=flat-square&logo=laravel)](https://laravel.com)
[![Node.js](https://img.shields.io/badge/Node.js-14+-339933?style=flat-square&logo=node.js)](https://nodejs.org)
[![WebSocket](https://img.shields.io/badge/WebSocket-Real--Time-010101?style=flat-square&logo=socket.io)](https://websocket.org)
[![MySQL](https://img.shields.io/badge/MySQL-8.0+-4479A1?style=flat-square&logo=mysql)](https://mysql.com)
[![Redis](https://img.shields.io/badge/Redis-Cache-DC382D?style=flat-square&logo=redis)](https://redis.io)

<div align="center">
  <img src="docs/images/user-interface/userinterface.png" alt="User Interface - Game Library" width="1200">
  <p><em>Beautiful and intuitive user interface with game library, easy navigation, and modern design</em></p>
</div>



https://github.com/user-attachments/assets/b87aef85-b5f3-4467-ac26-bf83f5a06f86



## 🎮 **Supported Game Types**

### **1. Slot Games** 🎰
- Classic 3-reel and 5-reel slots
- Multiple paylines and bet levels
- Free spins, bonus rounds, and multipliers
- Gamble features
- Progressive jackpots

<div align="center">
  <img src="docs/images/games/slot-game-1.png" alt="Slot Game Example 1" width="1000">
  <p><em>Premium slot games with stunning graphics and exciting features</em></p>
</div>

#### **Slot Game Gallery**

<div align="center">
  
| | | |
|:---:|:---:|:---:|
| <img src="docs/images/games/slot-game-2.png" alt="Slot Game 2" width="300"> | <img src="docs/images/games/slot-game-3.png" alt="Slot Game 3" width="300"> | <img src="docs/images/games/slot-game-4.png" alt="Slot Game 4" width="300"> |
| <img src="docs/images/games/slot-game-5.png" alt="Slot Game 5" width="300"> | <img src="docs/images/games/slot-game-6.png" alt="Slot Game 6" width="300"> | <img src="docs/images/games/slot-game-7.png" alt="Slot Game 7" width="300"> |
| <img src="docs/images/games/slot-game-8.png" alt="Slot Game 8" width="300"> | <img src="docs/images/games/slot-game-9.png" alt="Slot Game 9" width="300"> | <img src="docs/images/games/slot-game-10.png" alt="Slot Game 10" width="300"> |
| <img src="docs/images/games/slot-game-11.png" alt="Slot Game 11" width="300"> | | |

<p><em>Diverse collection of premium slot games with various themes and features</em></p>

</div>

### **2. Arcade Games** 🕹️
- Action-packed arcade experiences
- Skill-based gameplay
- Tournament support
- Leaderboards and achievements

<!-- Add arcade game screenshot here -->
<!-- <div align="center">
  <img src="docs/images/games/arcade-game.png" alt="Arcade Game" width="800">
</div> -->

### **3. Fishing Games** 🎣
- Multiplayer fishing game
- Real-time multiplayer rooms (up to 6 players)
- Dynamic fish spawning with scripts
- Boss fish and special events
- Auto-fire and manual shooting modes
- Tide system for dynamic gameplay

<div align="center">
  <img src="docs/images/games/fishing_game.png" alt="Fishing Game - BuffaloThunder" width="1200">
  <p><em>Premium multiplayer fishing game with real-time action, boss fish, and exciting gameplay features</em></p>
</div>

### **4. Custom Games** 🎲
- Easy integration for new game types
- Flexible game room system
- Customizable game logic
- Plugin architecture

---

## 🚀 **Quick Start Guide**

### **Prerequisites**

- PHP 8.2 or higher
- Node.js 14 or higher
- MySQL 8.0 or higher
- Redis 6.0 or higher
- Composer (PHP dependency manager)
- NPM (Node.js package manager)

### **Installation Steps**

#### **1. Clone and Install Dependencies**

```bash
# Install PHP dependencies
composer install

# Install Node.js dependencies for WebSocket server
cd PTWebSocket/Fishing
npm install
```

#### **2. Configure Environment**

```bash
# Copy environment file
cp .env.example .env

# Generate application key
php artisan key:generate

# Configure database and Redis settings in .env
```

#### **3. Setup Database**

```bash
# Run migrations
php artisan migrate

# Seed initial data (optional)
php artisan db:seed
```

#### **4. Configure WebSocket Server**

Edit `public/arcade_config.json`:

```json
{
    "port": 8010,
    "host": "your-server-ip",
    "prefix": "http://",
    "host_ws": "your-server-ip",
    "prefix_ws": "ws://",
    "ssl": false
}
```

#### **5. Start Services**

```bash
# Start Laravel development server
php artisan serve

# Start WebSocket server (in separate terminal)
cd PTWebSocket/Fishing
node Arcade.js
```

#### **6. Access the Platform**

- **Frontend**: `http://localhost:8000`
- **WebSocket Server**: `ws://your-server-ip:8010/websocket`

---

## 📋 **Complete Workflow**

### **Player Journey**

1. **User Registration/Login** → Laravel authenticates and creates session
2. **Game Selection** → User browses available games
3. **Game Loading** → Laravel serves game iframe with configuration
4. **WebSocket Connection** → Game connects to real-time server
5. **Room Assignment** → Server assigns player to appropriate game room
6. **Real-Time Gameplay** → Player interacts with game, balance updates instantly
7. **Balance Sync** → Changes sync to Redis cache and MySQL database

### **Technical Flow**

```
User Login
    ↓
Laravel Authentication
    ↓
Game Selection → Load Game View
    ↓
Game Client Initializes
    ↓
Read arcade_config.json → Get WebSocket URL
    ↓
Connect to WebSocket Server
    ↓
Authentication Message → Server Validates
    ↓
Create/Find Game Room → Assign Player
    ↓
Game Loop Starts → Real-Time Gameplay
    ↓
Balance Updates (Redis → MySQL → Client)
```

---

## 🔧 **Configuration & Setup**

### **WebSocket Server Configuration**

**File**: `public/arcade_config.json`

```json
{
    "port": 8010,
    "host": "ip or domain",
    "prefix": "http://",
    "host_ws": "ip or domain",
    "prefix_ws": "ws://",
    "ssl": false
}
```

### **Database Configuration**

**File**: `PTWebSocket/Fishing/DBConn.js` (or environment variables)

```javascript
{
    host: process.env.DB_HOST || 'localhost',
    user: process.env.DB_USERNAME || 'root',
    password: process.env.DB_PASSWORD || '',
    database: process.env.DB_DATABASE || 'slotgame',
    port: process.env.DB_PORT || '3306'
}
```

### **Redis Configuration**

**File**: `PTWebSocket/Fishing/RedisBridge.js`

- Default: `localhost:6379`
- Configurable via environment variables

---

## 🎯 **Running in Production**

### **Windows Server**

```bash
# Start WebSocket server
cd PTWebSocket
start_arcade.bat
```

### **Linux/VPS**

```bash
# Make script executable
chmod +x PTWebSocket/start_arcade.sh

# Start server
./PTWebSocket/start_arcade.sh

# Or run in background
cd PTWebSocket/Fishing
nohup node Arcade.js > arcade.log 2>&1 &
```

### **Process Management (PM2)**

```bash
# Install PM2
npm install -g pm2

# Start WebSocket server with PM2
cd PTWebSocket/Fishing
pm2 start Arcade.js --name "game-server"

# Save PM2 configuration
pm2 save

# Setup PM2 to start on boot
pm2 startup
```

### **Firewall Configuration**

```bash
# Allow WebSocket port (Linux)
sudo ufw allow 8010/tcp

# Or with iptables
sudo iptables -A INPUT -p tcp --dport 8010 -j ACCEPT
```

---

## 💾 **Database & Caching**

### **MySQL Database**

**Key Tables**:
- `w_users` - User accounts and balances
- `w_statistics` - Game statistics and analytics
- `w_game_bank` - Game bank balances
- `w_shops` - Shop/location management

**Features**:
- Connection pooling (5 connections)
- Transaction support
- Optimized queries for high performance

### **Redis Cache**

**Cache Keys**:
- `player_balance_{userId}` - Cached player balance
- `player_bet_{userId}` - Current session bet total
- `player_win_{userId}` - Current session win total
- `player_total_bet_{userId}` - Lifetime bet total
- `player_total_win_{userId}` - Lifetime win total
- `shop_{shopId}` - Shop configuration cache

**Benefits**:
- Sub-millisecond balance updates
- Session tracking
- Distributed locking for concurrent updates
- Reduced database load

### **Balance Update Flow**

```
Player Action (Shoot/Bet)
    ↓
Deduct from Redis Balance (Instant)
    ↓
Process Game Logic
    ↓
Calculate Win
    ↓
Add Win to Redis Balance (Instant)
    ↓
Update MySQL Database (Async)
    ↓
Send Updated Balance to Client
```

---

## 🎮 **Game Room Management**

### **Room Types**

- **Slot Games**: Single-player rooms
- **Arcade Games**: Single-player or tournament rooms
- **Fishing Games**: Multiplayer rooms (up to 6 players per room)

### **Room Lifecycle**

1. **Creation**: Automatically created when needed
2. **Player Assignment**: Players join available seats
3. **Game Loop**: Runs every second, spawning events and managing gameplay
4. **Cleanup**: Rooms are destroyed 30 minutes after last player leaves

### **Features**

- **Auto-Scaling**: New rooms created when existing ones are full
- **Reconnection Support**: Players can reconnect to their session
- **Dynamic Scripts**: Game events triggered by scripts (boss fish, tides, etc.)
- **Resource Management**: Efficient cleanup of unused resources

---

## 🔍 **Troubleshooting**

### **Game Won't Connect to WebSocket**

**Symptoms**: Game shows "WebSocket connection failed"

**Solutions**:
1. ✅ Verify WebSocket server is running: `ps aux | grep "node Arcade.js"`
2. ✅ Check port 8010 is open: `netstat -an | grep 8010`
3. ✅ Verify firewall allows port 8010
4. ✅ Check `arcade_config.json` has correct IP and port
5. ✅ Ensure Redis is running: `redis-cli ping`

### **Balance Not Updating**

**Symptoms**: Balance doesn't change after wins/bets

**Solutions**:
1. ✅ Verify MySQL connection in `DBConn.js`
2. ✅ Check Redis is running and accessible
3. ✅ Verify player is in correct game room
4. ✅ Check server logs for balance update errors

### **Fish/Events Not Spawning**

**Symptoms**: Game loads but no events appear

**Solutions**:
1. ✅ Verify `GameRoomBF` is created successfully
2. ✅ Check game loop is running (should log every second)
3. ✅ Verify fish data files exist: `arcade_data/fish.json`, `arcade_data/fishBF.json`
4. ✅ Check game script is initialized correctly

---

## 📊 **Performance & Scalability**

### **Performance Metrics**

- **WebSocket Latency**: < 50ms average
- **Balance Updates**: < 10ms (Redis cached)
- **Database Queries**: Optimized with connection pooling
- **Concurrent Players**: Supports thousands of simultaneous connections

### **Scalability Features**

- **Horizontal Scaling**: Multiple WebSocket server instances
- **Load Balancing**: Distribute players across servers
- **Redis Clustering**: Scale cache layer independently
- **Database Replication**: Read replicas for analytics

---

## 🔒 **Security Features**

- ✅ **Secure Authentication**: Laravel Sanctum and JWT tokens
- ✅ **Balance Protection**: Distributed locking prevents race conditions
- ✅ **Input Validation**: All user inputs validated and sanitized
- ✅ **SQL Injection Protection**: Parameterized queries
- ✅ **XSS Protection**: Output escaping and sanitization
- ✅ **CSRF Protection**: Laravel CSRF tokens
- ✅ **Session Security**: Secure session management

---

## 📈 **Analytics & Reporting**

### **Available Statistics**

- Player activity and session data
- Game performance metrics (RTP, bet/wins)
- Revenue analytics
- Shop/location performance
- Tournament results
- Jackpot tracking

### **Reporting Features**

- Real-time dashboards
- Exportable reports (CSV, Excel)
- Custom date ranges
- Multi-shop aggregation
- Player behavior analysis

---

## 🌍 **Multi-Language Support**

The platform supports multiple languages:
- English
- German
- Serbian
- And more (easily extensible)

---

## 📞 **Support & Documentation**

### **Getting Help**

- 📖 **Technical Documentation**: See sections below for detailed workflows
- 🐛 **Issue Reporting**: Check logs in `storage/logs/`
- 🔧 **Configuration**: Review configuration files in `config/` and `PTWebSocket/Fishing/`

### **Key Files Reference**

| File | Purpose |
|------|---------|
| `public/arcade_config.json` | WebSocket server configuration |
| `PTWebSocket/Fishing/Arcade.js` | Main WebSocket server |
| `PTWebSocket/Fishing/DBConn.js` | Database connection |
| `PTWebSocket/Fishing/RedisBridge.js` | Redis integration |
| `app/Http/Controllers/Web/Frontend/GamesController.php` | Game loading controller |
| `app/Games/Game/Server.php` | Game API endpoints |

---

## 🎯 **Use Cases**

### **For Casino Operators**

- Launch a complete online casino platform
- Offer multiple game types to attract diverse players
- Scale operations across multiple locations
- Track performance with comprehensive analytics
- Manage player balances and transactions securely

### **For Game Developers**

- Integrate new games using our flexible architecture
- Leverage real-time multiplayer capabilities
- Use our balance management system
- Access player analytics and statistics

### **For Business Owners**

- Reduce development time with pre-built infrastructure
- Lower operational costs with efficient architecture
- Increase player engagement with social gaming features
- Make data-driven decisions with comprehensive analytics
- **Customize everything** to match your brand and business model
- **White-label solution** - Make it completely your own
- **Professional support** for custom development and integration

---

## 🚀 **Next Steps**

1. **Review Configuration**: Customize settings for your environment
2. **Deploy Services**: Set up Laravel, WebSocket server, MySQL, and Redis
3. **Test Games**: Verify all game types work correctly
4. **Configure Analytics**: Set up reporting and dashboards
5. **Go Live**: Launch your casino platform!

---

## 📝 **License & Credits**

This is a professional casino gaming platform built with modern technologies.

**Technologies Used**:
- Laravel Framework
- Node.js & WebSocket
- MySQL Database
- Redis Cache
- Egret Engine (for HTML5 games)

---

## 🎉 **Ready to Get Started?**

Transform your casino business today with our enterprise-grade gaming platform. Whether you're launching a new casino or upgrading your existing platform, our solution provides everything you need for success.

**Key Benefits**:
- ✅ Production-ready codebase
- ✅ Scalable architecture
- ✅ Real-time multiplayer support
- ✅ Comprehensive feature set
- ✅ Easy to deploy and maintain

---

<div align="center">

**Built with ❤️ for the Gaming Industry**

*For technical support and detailed documentation, refer to the sections above.*

</div>

---

## 📚 **Detailed Technical Documentation**

<details>
<summary><b>Click to expand detailed technical workflow</b></summary>

### **Step-by-Step Workflow**

#### **Step 1: User Accesses Game**

1. User logs in to Laravel application (`/login`)
2. User navigates to game list or directly to a specific game
3. Laravel route (`/game/{game}`) loads the game view

**Route**: `routes/web.php` → `GamesController@go()`

#### **Step 2: Laravel Loads Game**

1. **Controller checks**:
   - User is authenticated
   - Game exists and is enabled
   - User has access to the game

2. **Creates SlotSettings instance**:
   ```php
   $slot = new \VanguardLTE\Games\Game\SlotSettings($game->name, $userId);
   ```

3. **Renders view**: `resources/views/frontend/games/list/Game.blade.php`
   - Creates an iframe pointing to: `/games/Game/www.goldentreasure.mobi/game/index.html`
   - Passes game parameters via URL query string:
     ```
     ?gameId=1028&uid=712&token=...&cdn=games/Game/cdn.goldentreasure.mobi
     ```

#### **Step 3: Game Client Initializes**

1. **Game HTML loads** (`index.html`)
2. **JavaScript overrides** (in `index.html`):
   - Intercepts WebSocket constructor
   - Reads `arcade_config.json` to get WebSocket URL
   - Overrides `egret.WebSocket`, `Global.gameSocketUrl`, `MySocket` to force correct URL
   - Prevents old cached URLs from being used

3. **Game engine (Egret) loads**:
   - Loads game assets from CDN
   - Initializes game scene
   - Sets up WebSocket connection

#### **Step 4: Game Connects to Backend API**

**File**: `public/games/Game/www.goldentreasure.mobi/game/skdm.js`

1. **`skdm.houtai()` function** makes AJAX call to Laravel:
   ```
   POST /game/Game/server?api=gamehoutai&url=...&stime=...&sign=...
   ```

2. **Laravel Server.php** handles request:
   - Validates user authentication
   - Returns game configuration
   - Returns WebSocket server information (from `arcade_config.json`)

3. **Response includes**:
   ```json
   {
     "Code": 20000,
     "Message": "登录成功",
     "Data": {
       "res": [{"gameid": 1004, "servid": 1}]
     }
   }
   ```

#### **Step 5: Game Connects to WebSocket Server**

1. **Game reads WebSocket URL** from:
   - `arcade_config.json` (via AJAX)
   - Response from Laravel API
   - JavaScript overrides ensure correct URL

2. **WebSocket connection**:
   ```
   ws://ip or domain:8010/websocket
   ```

3. **Connection process**:
   - Game creates WebSocket instance
   - Sends authentication message
   - WebSocket server validates and creates Player instance

#### **Step 6: WebSocket Server Handles Connection**

**File**: `PTWebSocket/Fishing/Arcade.js`

1. **Server listens** on port 8010:
   ```javascript
   server.listen(serverConfig.port, '0.0.0.0', function() {
       console.log('WebSocket server listening on 0.0.0.0:' + serverConfig.port);
   });
   ```

2. **Upgrade HTTP to WebSocket**:
   - Server intercepts HTTP upgrade request
   - Creates WebSocket connection
   - Routes to appropriate handler (`wss_game` or `wss_auth`)

3. **Message handling**:
   - Receives JSON messages from client
   - Routes to appropriate kernel (`KernelGF` for Game)
   - Kernel processes game actions (shoot, hit fish, etc.)

#### **Step 7: Player Joins Game Room**

**File**: `PTWebSocket/Fishing/Arcade.js` → `GameRoomManager.addClient()`

1. **Finds or creates game room**:
   - Checks existing rooms for available seats
   - If full, creates new `GameRoomBF` instance
   - Assigns player to room

2. **GameRoomBF initialization**:
   - Loads fish data from JSON files
   - Sets up game scripts (tides, boss fish, etc.)
   - Starts game loop (runs every 1 second)

3. **Player initialization**:
   - Creates `Player` instance
   - Loads balance from MySQL/Redis
   - Assigns seat ID
   - Sends initial game state to client

#### **Step 8: Real-Time Gameplay**

**Game Loop** (runs every 1 second in `GameRoomBF.run()`):

1. **Fish spawning**:
   - Generates fish based on script/tide
   - Sends fish positions to all players in room

2. **Player actions**:
   - **Shoot**: Player sends bullet message → Server validates → Deducts bet → Checks hit
   - **Hit Fish**: Server calculates win → Updates balance → Sends win message
   - **Auto Fire**: Server handles continuous shooting

3. **Balance updates**:
   - **Redis**: Cached balance for fast access
   - **MySQL**: Persistent storage (updated periodically)
   - **Laravel**: Final balance source of truth

4. **Game events**:
   - Boss fish spawning
   - Tide changes
   - Special events (fire storm, etc.)

#### **Step 9: Balance Synchronization**

**Three-tier balance system**:

1. **Client-side**: Displayed balance (updated via WebSocket messages)
2. **Redis**: Fast cache (updated on every bet/win)
3. **MySQL**: Persistent storage (updated via `updateBankDirect()`)

**Flow**:
```
Player shoots → Deduct bet from Redis → Check hit → Add win to Redis → 
Update MySQL → Send balance to client
```

### **WebSocket Message Format**

**Authentication**:
```json
{
  "sys": "fish",
  "cmd": "auth",
  "data": {
    "ark_id": 712,
    "gameid": 1004,
    "servid": 1
  }
}
```

**Shoot**:
```json
{
  "sys": "fish",
  "cmd": "shoot",
  "data": {
    "bulletid": "1_123456",
    "angle": 45,
    "pos": 1
  }
}
```

**Hit Fish**:
```json
{
  "sys": "fish",
  "cmd": "hitsprites",
  "data": {
    "bulletid": "1_123456",
    "fblist": [{"fishid": 1001, "bulletid": "1_123456"}]
  }
}
```

</details>

---

<div align="center">

**🎰 Ready to revolutionize your casino platform? Get started today! 🚀**

</div>
