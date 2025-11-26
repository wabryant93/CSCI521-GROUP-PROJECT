<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VIBE - Event Management Platform</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .navbar {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 1rem 2rem;
            box-shadow: 0 2px 20px rgba(0,0,0,0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-links a {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: #667eea;
        }

        .auth-buttons {
            display: flex;
            gap: 1rem;
        }

        .btn {
            padding: 0.6rem 1.5rem;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
        }

        .btn-primary {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .btn-secondary {
            background: transparent;
            border: 2px solid #667eea;
            color: #667eea;
        }

        .container {
            max-width: 1400px;
            margin: 2rem auto;
            padding: 0 2rem;
        }

        .dashboard {
            display: grid;
            grid-template-columns: 250px 1fr;
            gap: 2rem;
            margin-top: 2rem;
        }

        .sidebar {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            height: fit-content;
        }

        .sidebar h3 {
            margin-bottom: 1.5rem;
            color: #333;
        }

        .sidebar-menu {
            list-style: none;
        }

        .sidebar-menu li {
            padding: 0.8rem 1rem;
            margin-bottom: 0.5rem;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .sidebar-menu li:hover,
        .sidebar-menu li.active {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .main-content {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .header-section {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
        }

        .search-bar {
            display: flex;
            gap: 1rem;
            flex: 1;
            max-width: 600px;
        }

        .search-bar input {
            flex: 1;
            padding: 0.8rem 1.5rem;
            border: 2px solid #e0e0e0;
            border-radius: 25px;
            font-size: 1rem;
        }

        .search-bar input:focus {
            outline: none;
            border-color: #667eea;
        }

        .filter-section {
            display: flex;
            gap: 1rem;
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .filter-btn {
            padding: 0.6rem 1.2rem;
            border: 2px solid #e0e0e0;
            background: white;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .filter-btn:hover,
        .filter-btn.active {
            background: #667eea;
            color: white;
            border-color: #667eea;
        }

        .events-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .event-card {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 3px 15px rgba(0,0,0,0.1);
            transition: all 0.3s;
            border: 2px solid #f0f0f0;
        }

        .event-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.15);
        }

        .event-image {
            width: 100%;
            height: 180px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 3rem;
        }

        .event-content {
            padding: 1.5rem;
        }

        .event-title {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
            color: #333;
        }

        .event-meta {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 1rem;
        }

        .event-meta span {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .event-tags {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
            margin-bottom: 1rem;
        }

        .tag {
            padding: 0.3rem 0.8rem;
            background: #f0f0f0;
            border-radius: 15px;
            font-size: 0.8rem;
            color: #667eea;
        }

        .event-actions {
            display: flex;
            gap: 0.5rem;
        }

        .btn-small {
            flex: 1;
            padding: 0.5rem 1rem;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
        }

        .btn-view {
            background: #667eea;
            color: white;
        }

        .btn-save {
            background: white;
            border: 2px solid #667eea;
            color: #667eea;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            max-width: 600px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: #333;
        }

        .form-group input,
        .form-group textarea,
        .form-group select {
            width: 100%;
            padding: 0.8rem;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 1rem;
        }

        .form-group textarea {
            resize: vertical;
            min-height: 100px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .stat-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 1.5rem;
            border-radius: 12px;
            text-align: center;
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .stat-label {
            font-size: 0.9rem;
            opacity: 0.9;
        }

        @media (max-width: 768px) {
            .dashboard {
                grid-template-columns: 1fr;
            }

            .sidebar {
                display: none;
            }

            .events-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
<nav class="navbar">
    <div class="logo">🎭 VIBE</div>
    <ul class="nav-links">
        <li><a href="VIBEhome.html">Home</a></li>
        <li><a href="VIBEevents.html">Events</a></li>
        <li><a href="VIBElogin.html">Profile</a></li>
        <li><a href="#VIBEabout.html">About</a></li>
    </ul>
    <div class="auth-buttons">
        <button class="btn btn-secondary" onclick="showLoginModal()">Login</button>
        <button class="btn btn-primary" onclick="showSignupModal()">Sign Up</button>
    </div>
</nav>

        <main class="main-content">
            <div class="header-section">
                <h2>Browse Upcoming Local Events</h2>
                <button class="btn btn-primary" onclick="showCreateEventModal()">+ Create Event</button>
            </div>

            <div class="search-bar">
                <input type="text" placeholder="Search events, artists, venues..." id="searchInput">
                <button class="btn btn-primary" onclick="searchEvents()">Search</button>
            </div>

            <div class="filter-section">
                <button class="filter-btn active">All Dates</button>
                <button class="filter-btn">Today</button>
                <button class="filter-btn">This Weekend</button>
                <button class="filter-btn">Next Week</button>
                <button class="filter-btn">This Month</button>
            </div>

            <div class="events-grid" id="eventsGrid">
                <!-- Sample Event Cards -->
                <div class="event-card">
                    <div class="event-image">🎵</div>
                    <div class="event-content">
                        <div class="event-title">Summer Music Festival</div>
                        <div class="event-meta">
                            <span>📅 July 15, 2024</span>
                            <span>📍 Central Park, NYC</span>
                            <span>💰 $45 - $120</span>
                        </div>
                        <div class="event-tags">
                            <span class="tag">Music</span>
                            <span class="tag">Festival</span>
                            <span class="tag">TicketMaster</span>
                        </div>
                        <div class="event-actions">
                            <button class="btn-small btn-view">View Details</button>
                            <button class="btn-small btn-save">Save</button>
                        </div>
                    </div>
                </div>

                <div class="event-card">
                    <div class="event-image">🏀</div>
                    <div class="event-content">
                        <div class="event-title">NBA Finals Game 5</div>
                        <div class="event-meta">
                            <span>📅 June 20, 2024</span>
                            <span>📍 Madison Square Garden</span>
                            <span>💰 $150 - $500</span>
                        </div>
                        <div class="event-tags">
                            <span class="tag">Sports</span>
                            <span class="tag">Basketball</span>
                            <span class="tag">TicketMaster</span>
                        </div>
                        <div class="event-actions">
                            <button class="btn-small btn-view">View Details</button>
                            <button class="btn-small btn-save">Save</button>
                        </div>
                    </div>
                </div>

                <div class="event-card">
                    <div class="event-image">🎭</div>
                    <div class="event-content">
                        <div class="event-title">Broadway Musical Night</div>
                        <div class="event-meta">
                            <span>📅 August 5, 2024</span>
                            <span>📍 Broadway Theatre</span>
                            <span>💰 $75 - $200</span>
                        </div>
                        <div class="event-tags">
                            <span class="tag">Theater</span>
                            <span class="tag">Musical</span>
                            <span class="tag">User Event</span>
                        </div>
                        <div class="event-actions">
                            <button class="btn-small btn-view">View Details</button>
                            <button class="btn-small btn-save">Save</button>
                        </div>
                    </div>
                </div>

                <div class="event-card">
                    <div class="event-image">🎨</div>
                    <div class="event-content">
                        <div class="event-title">Art Gallery Opening</div>
                        <div class="event-meta">
                            <span>📅 July 1, 2024</span>
                            <span>📍 MOMA, NYC</span>
                            <span>💰 Free</span>
                        </div>
                        <div class="event-tags">
                            <span class="tag">Art</span>
                            <span class="tag">Exhibition</span>
                            <span class="tag">User Event</span>
                        </div>
                        <div class="event-actions">
                            <button class="btn-small btn-view">View Details</button>
                            <button class="btn-small btn-save">Save</button>
                        </div>
                    </div>
                </div>
            </div>
        </main>
    </div>
</div>

<!-- Create Event Modal -->
<div class="modal" id="createEventModal">
    <div class="modal-content">
        <h2>Create New Event</h2>
        <form id="createEventForm">
            <div class="form-group">
                <label>Event Name</label>
                <input type="text" name="name" placeholder="Enter event name" required>
            </div>
            <div class="form-group">
                <label>Category</label>
                <select name="category" required>
                    <option>Music</option>
                    <option>Sports</option>
                    <option>Arts & Theater</option>
                    <option>Family</option>
                    <option>Comedy</option>
                    <option>Other</option>
                </select>
            </div>
            <div class="form-group">
                <label>Date & Time</label>
                <input type="datetime-local" name="datetime" required>
            </div>
            <div class="form-group">
                <label>Location</label>
                <input type="text" name="location" placeholder="Venue or address" required>
            </div>
            <div class="form-group">
                <label>Description</label>
                <textarea name="description" placeholder="Event description"></textarea>
            </div>
            <div class="form-group">
                <label>Price Range</label>
                <input type="text" name="price" placeholder="e.g., $20 - $50 or Free">
            </div>
            <div style="display: flex; gap: 1rem;">
                <button type="button" class="btn btn-secondary" onclick="closeModal('createEventModal')" style="flex: 1;">Cancel</button>
                <button type="submit" class="btn btn-primary" style="flex: 1;">Create Event</button>
            </div>
        </form>
    </div>
</div>

<!-- Login Modal -->
<div class="modal" id="loginModal">
    <div class="modal-content">
        <h2>Login to VIBE</h2>
        <form id="loginForm">
            <div class="form-group">
                <label>Email</label>
                <input type="email" name="email" placeholder="Enter your email" required>
            </div>
            <div class="form-group">
                <label>Password</label>
                <input type="password" name="password" placeholder="Enter your password" required>
            </div>
            <div style="display: flex; gap: 1rem;">
                <button type="button" class="btn btn-secondary" onclick="closeModal('loginModal')" style="flex: 1;">Cancel</button>
                <button type="submit" class="btn btn-primary" style="flex: 1;">Login</button>
            </div>
        </form>
    </div>
</div>

<!-- Signup Modal -->
<div class="modal" id="signupModal">
    <div class="modal-content">
        <h2>Join VIBE</h2>
        <form id="signupForm">
            <div class="form-group">
                <label>Full Name</label>
                <input type="text" name="name" placeholder="Enter your name" required>
            </div>
            <div class="form-group">
                <label>Email</label>
                <input type="email" name="email" placeholder="Enter your email" required>
            </div>
            <div class="form-group">
                <label>Password</label>
                <input type="password" name="password" placeholder="Create a password" required>
            </div>
            <div class="form-group">
                <label>Confirm Password</label>
                <input type="password" name="confirmPassword" placeholder="Confirm your password" required>
            </div>
            <div style="display: flex; gap: 1rem;">
                <button type="button" class="btn btn-secondary" onclick="closeModal('signupModal')" style="flex: 1;">Cancel</button>
                <button type="submit" class="btn btn-primary" style="flex: 1;">Sign Up</button>
            </div>
        </form>
    </div>
</div>

<script>
    // ============================================
    // TICKETMASTER API CONFIGURATION
    // ============================================
    const TICKETMASTER_API_KEY = 'YOUR_API_KEY_HERE'; // Get from: https://developer.ticketmaster.com/
    const TICKETMASTER_BASE_URL = 'https://app.ticketmaster.com/discovery/v2';

    // ============================================
    // TICKETMASTER API FUNCTIONS
    // ============================================

    // Fetch events from TicketMaster API
    async function fetchTicketMasterEvents(keyword = '', city = '', startDate = '', size = 20) {
        try {
            const params = new URLSearchParams({
                apikey: TICKETMASTER_API_KEY,
                keyword: keyword,
                city: city,
                size: size,
                sort: 'date,asc'
            });

            if (startDate) {
                params.append('startDateTime', startDate);
            }

            const response = await fetch(`${TICKETMASTER_BASE_URL}/events.json?${params}`);
            const data = await response.json();

            if (data._embedded && data._embedded.events) {
                return data._embedded.events;
            }
            return [];
        } catch (error) {
            console.error('Error fetching TicketMaster events:', error);
            return [];
        }
    }

    // Load TicketMaster events on page load
    async function loadTicketMasterEvents() {
        const events = await fetchTicketMasterEvents('', '', '', 12);
        displayTicketMasterEvents(events);
    }

    // Display TicketMaster events in the grid
    function displayTicketMasterEvents(events) {
        const eventsGrid = document.getElementById('eventsGrid');

        events.forEach(event => {
            const eventCard = createTicketMasterEventCard(event);
            eventsGrid.appendChild(eventCard);
        });
    }

    // Create event card from TicketMaster data
    function createTicketMasterEventCard(event) {
        const card = document.createElement('div');
        card.className = 'event-card';

        // Get event details
        const name = event.name;
        const date = new Date(event.dates.start.localDate).toLocaleDateString('en-US', {
            year: 'numeric',
            month: 'long',
            day: 'numeric'
        });
        const venue = event._embedded?.venues?.[0]?.name || 'TBA';
        const city = event._embedded?.venues?.[0]?.city?.name || '';
        const priceRange = event.priceRanges ?
            `${event.priceRanges[0].min} - ${event.priceRanges[0].max}` :
            'Price TBA';
        const category = event.classifications?.[0]?.segment?.name || 'Other';
        const imageUrl = event.images?.[0]?.url || '';
        const ticketUrl = event.url;

        // Get emoji based on category
        const categoryEmojis = {
            'Music': '🎵',
            'Sports': '🏀',
            'Arts & Theatre': '🎭',
            'Film': '🎬',
            'Family': '👨‍👩‍👧‍👦',
            'Miscellaneous': '🎪'
        };
        const emoji = categoryEmojis[category] || '🎉';

        card.innerHTML = `
                <div class="event-image" style="${imageUrl ? `background-image: url(${imageUrl}); background-size: cover; background-position: center;` : ''}">${!imageUrl ? emoji : ''}</div>
                <div class="event-content">
                    <div class="event-title">${name}</div>
                    <div class="event-meta">
                        <span>📅 ${date}</span>
                        <span>📍 ${venue}${city ? ', ' + city : ''}</span>
                        <span>💰 ${priceRange}</span>
                    </div>
                    <div class="event-tags">
                        <span class="tag">${category}</span>
                        <span class="tag">TicketMaster</span>
                    </div>
                    <div class="event-actions">
                        <button class="btn-small btn-view" onclick="window.open('${ticketUrl}', '_blank')">Buy Tickets</button>
                        <button class="btn-small btn-save" onclick="saveEvent('${event.id}', 'ticketmaster')">Save</button>
                    </div>
                </div>
            `;

        return card;
    }

    // Save event to database (integrate with your JDBC backend)
    async function saveEvent(eventId, source) {
        // Send to your backend API that connects to Oracle via JDBC
        try {
            const response = await fetch('/api/events/save', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({
                    eventId: eventId,
                    source: source,
                    userId: getCurrentUserId() // Implement this function
                })
            });

            if (response.ok) {
                alert('Event saved successfully!');
            } else {
                alert('Failed to save event');
            }
        } catch (error) {
            console.error('Error saving event:', error);
            alert('Error saving event. Make sure backend is running.');
        }
    }

    // Get current user ID (implement based on your auth system)
    function getCurrentUserId() {
        // This should retrieve the logged-in user's ID
        // For now, return a placeholder
        return sessionStorage.getItem('userId') || null;
    }

    // ============================================
    // MODAL FUNCTIONS
    // ============================================

    function showCreateEventModal() {
        document.getElementById('createEventModal').classList.add('active');
    }

    function showLoginModal() {
        document.getElementById('loginModal').classList.add('active');
    }

    function showSignupModal() {
        document.getElementById('signupModal').classList.add('active');
    }

    function closeModal(modalId) {
        document.getElementById(modalId).classList.remove('active');
    }

    // Close modal on outside click
    document.querySelectorAll('.modal').forEach(modal => {
        modal.addEventListener('click', (e) => {
            if (e.target === modal) {
                modal.classList.remove('active');
            }
        });
    });

    // ============================================
    // SEARCH FUNCTION (TICKETMASTER + DATABASE)
    // ============================================

    async function searchEvents() {
        const query = document.getElementById('searchInput').value;
        const eventsGrid = document.getElementById('eventsGrid');

        // Clear existing events
        eventsGrid.innerHTML = '';

        // Search TicketMaster
        const tmEvents = await fetchTicketMasterEvents(query);
        displayTicketMasterEvents(tmEvents);

        // Also search your database for user-created events
        await searchUserEvents(query);
    }

    // Search user-created events from database
    async function searchUserEvents(query) {
        try {
            const response = await fetch(`/api/events/search?query=${encodeURIComponent(query)}`);
            const userEvents = await response.json();

            const eventsGrid = document.getElementById('eventsGrid');
            userEvents.forEach(event => {
                const card = createUserEventCard(event);
                eventsGrid.appendChild(card);
            });
        } catch (error) {
            console.error('Error searching user events:', error);
        }
    }

    // Create event card for user-created events
    function createUserEventCard(event) {
        const card = document.createElement('div');
        card.className = 'event-card';

        card.innerHTML = `
                <div class="event-image">${event.emoji || '🎉'}</div>
                <div class="event-content">
                    <div class="event-title">${event.name}</div>
                    <div class="event-meta">
                        <span>📅 ${event.date}</span>
                        <span>📍 ${event.location}</span>
                        <span>💰 ${event.price}</span>
                    </div>
                    <div class="event-tags">
                        <span class="tag">${event.category}</span>
                        <span class="tag">User Event</span>
                    </div>
                    <div class="event-actions">
                        <button class="btn-small btn-view" onclick="viewEventDetails('${event.id}')">View Details</button>
                        <button class="btn-small btn-save" onclick="saveEvent('${event.id}', 'user')">Save</button>
                    </div>
                </div>
            `;

        return card;
    }

    function viewEventDetails(eventId) {
        // Implement event details view
        console.log('Viewing event:', eventId);
    }

    // Form Submissions
    document.getElementById('createEventForm').addEventListener('submit', async (e) => {
        e.preventDefault();

        // Collect form data
        const formData = new FormData(e.target);
        const eventData = {
            name: formData.get('name'),
            category: formData.get('category'),
            datetime: formData.get('datetime'),
            location: formData.get('location'),
            description: formData.get('description'),
            price: formData.get('price'),
            userId: getCurrentUserId()
        };

        // Send to backend (Oracle JDBC)
        try {
            const response = await fetch('/api/events/create', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(eventData)
            });

            if (response.ok) {
                alert('Event created successfully!');
                closeModal('createEventModal');
                // Reload events
                loadAllEvents();
            } else {
                alert('Failed to create event');
            }
        } catch (error) {
            console.error('Error creating event:', error);
            alert('Error creating event. Make sure backend is running.');
        }
    });

    document.getElementById('loginForm').addEventListener('submit', async (e) => {
        e.preventDefault();

        const formData = new FormData(e.target);
        const credentials = {
            email: formData.get('email'),
            password: formData.get('password')
        };

        // Authenticate against Oracle Database via JDBC
        try {
            const response = await fetch('/api/auth/login', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(credentials)
            });

            if (response.ok) {
                const data = await response.json();
                sessionStorage.setItem('userId', data.userId);
                sessionStorage.setItem('token', data.token);
                alert('Login successful!');
                closeModal('loginModal');
                // Update UI for logged-in user
                updateAuthUI();
            } else {
                alert('Invalid credentials');
            }
        } catch (error) {
            console.error('Error logging in:', error);
            alert('Error logging in. Make sure backend is running.');
        }
    });

    document.getElementById('signupForm').addEventListener('submit', async (e) => {
        e.preventDefault();

        const formData = new FormData(e.target);
        const userData = {
            name: formData.get('name'),
            email: formData.get('email'),
            password: formData.get('password'),
            confirmPassword: formData.get('confirmPassword')
        };

        if (userData.password !== userData.confirmPassword) {
            alert('Passwords do not match!');
            return;
        }

        // Save to Oracle Database via JDBC
        try {
            const response = await fetch('/api/auth/signup', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(userData)
            });

            if (response.ok) {
                alert('Registration successful! Please login.');
                closeModal('signupModal');
                showLoginModal();
            } else {
                alert('Registration failed');
            }
        } catch (error) {
            console.error('Error signing up:', error);
            alert('Error signing up. Make sure backend is running.');
        }
    });

    function updateAuthUI() {
        // Update UI to show logged-in state
        const userId = sessionStorage.getItem('userId');
        if (userId) {
            // Hide login/signup, show user menu
            console.log('User logged in:', userId);
        }
    }

    // ============================================
    // LOAD ALL EVENTS (TICKETMASTER + USER EVENTS)
    // ============================================

    async function loadAllEvents() {
        const eventsGrid = document.getElementById('eventsGrid');
        eventsGrid.innerHTML = '';

        // Load TicketMaster events
        await loadTicketMasterEvents();

        // Load user-created events from database
        await loadUserCreatedEvents();
    }

    async function loadUserCreatedEvents() {
        try {
            const response = await fetch('/api/events/user-created');
            const userEvents = await response.json();

            userEvents.forEach(event => {
                const card = createUserEventCard(event);
                document.getElementById('eventsGrid').appendChild(card);
            });
        } catch (error) {
            console.error('Error loading user events:', error);
        }
    }

    // ============================================
    // INITIALIZE APP ON PAGE LOAD
    // ============================================

    window.addEventListener('DOMContentLoaded', () => {
        // Load initial events
        loadAllEvents();

        // Check if user is logged in
        updateAuthUI();
    });

    // Filter buttons
    document.querySelectorAll('.filter-btn').forEach(btn => {
        btn.addEventListener('click', () => {
            document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
            btn.classList.add('active');
        });
    });

    // Sidebar menu
    document.querySelectorAll('.sidebar-menu li').forEach(item => {
        item.addEventListener('click', () => {
            document.querySelectorAll('.sidebar-menu li').forEach(i => i.classList.remove('active'));
            item.classList.add('active');
        });
    });
</script>
</body>
</html>
