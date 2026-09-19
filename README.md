import './style.css'

const workouts = [
  { id: 'power', title: 'Full body power', category: 'Strength', duration: '32 min', level: 'Intermediate', image: 'https://images.unsplash.com/photo-1581009146145-b5ef050c2e1e?auto=format&fit=crop&w=900&q=85', accent: 'lime' },
  { id: 'flow', title: 'Reset & flow', category: 'Mobility', duration: '18 min', level: 'All levels', image: 'https://images.unsplash.com/photo-1545205597-3d9d02c29597?auto=format&fit=crop&w=900&q=85', accent: 'coral' },
  { id: 'run', title: 'Run your rhythm', category: 'Cardio', duration: '24 min', level: 'Beginner', image: 'https://images.unsplash.com/photo-1552674605-db6ffd4facb5?auto=format&fit=crop&w=900&q=85', accent: 'blue' },
]

const icon = (name, size = 20) => {
  const paths = {
    grid: '<rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/>',
    chart: '<path d="M4 19V5"/><path d="M4 19h16"/><path d="m7 15 3-4 3 2 5-7"/>',
    calendar: '<rect x="3" y="4" width="18" height="17" rx="2"/><path d="M16 2v4M8 2v4M3 10h18"/>',
    bookmark: '<path d="M6 3a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v19l-6-4-6 4Z"/>',
    settings: '<circle cx="12" cy="12" r="3.5"/><path d="m19.4 15 .1.1a2 2 0 1 1-2.8 2.8l-.1-.1a2 2 0 0 0-3.4 1.4v.3a2 2 0 1 1-4 0v-.2a2 2 0 0 0-3.4-1.4l-.1.1a2 2 0 1 1-2.8-2.8l.1-.1A2 2 0 0 0 1.7 12a2 2 0 1 1 0-4h.2a2 2 0 0 0 1.4-3.4l-.1-.1A2 2 0 1 1 6 1.7l.1.1A2 2 0 0 0 9.5.4V.2a2 2 0 1 1 4 0v.2a2 2 0 0 0 3.4 1.4l.1-.1a2 2 0 1 1 2.8 2.8l-.1.1A2 2 0 0 0 21.2 8h.3a2 2 0 1 1 0 4h-.2a2 2 0 0 0-1.9 3Z"/>',
    play: '<path d="m8 5 11 7-11 7Z"/>',
    arrow: '<path d="M5 12h14M13 6l6 6-6 6"/>',
    search: '<circle cx="11" cy="11" r="7"/><path d="m20 20-4-4"/>',
    heart: '<path d="M20.8 8.8c0 5.3-8.8 10.2-8.8 10.2S3.2 14.1 3.2 8.8A4.6 4.6 0 0 1 12 6.4a4.6 4.6 0 0 1 8.8 2.4Z"/>',
  }
  return `<svg width="${size}" height="${size}" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">${paths[name]}</svg>`
}

document.querySelector('#app').innerHTML = `
  <aside class="sidebar">
    <a class="brand" href="#" aria-label="Pulse home"><span class="brand-mark">+</span><span>pulse</span></a>
    <nav class="main-nav" aria-label="Main navigation">
      <a class="nav-link active" href="#dashboard">${icon('grid')}<span>Dashboard</span></a>
      <a class="nav-link" href="#progress">${icon('chart')}<span>My progress</span></a>
      <a class="nav-link" href="#schedule">${icon('calendar')}<span>Schedule</span><span class="nav-count">3</span></a>
      <a class="nav-link" href="#saved">${icon('bookmark')}<span>Saved workouts</span></a>
    </nav>
    <div class="sidebar-bottom">
      <div class="coach-card"><span class="coach-label">YOUR COACH</span><strong>Keep showing up.</strong><p>Consistency beats intensity.</p><div class="coach-dots"><i></i><i></i><i></i><i></i><i></i></div></div>
      <a class="nav-link" href="#settings">${icon('settings')}<span>Settings</span></a>
      <div class="profile"><div class="avatar">AM</div><div><strong>Alex Morgan</strong><small>Member since 2024</small></div><span class="profile-more">•••</span></div>
    </div>
  </aside>
  <main class="content" id="dashboard">
    <header class="topbar"><div class="mobile-brand"><span class="brand-mark">+</span> pulse</div><div class="welcome"><span>MONDAY, SEPTEMBER 22</span><h1>Good morning, Alex <span>✦</span></h1></div><div class="top-actions"><button class="icon-button" aria-label="Search">${icon('search')}</button><button class="icon-button has-dot" aria-label="Notifications">◌</button><div class="top-avatar">AM</div></div></header>
    <section class="hero-grid"><div class="hero-copy"><p class="eyebrow">YOUR DAILY FOCUS</p><h2>Move with<br><em>intention.</em></h2><p class="hero-description">A little movement today is a big win for your future self.</p><button class="primary-button" data-action="start-hero">Start today’s session ${icon('arrow', 18)}</button></div><div class="hero-visual"><div class="hero-image"></div><div class="hero-sticker">01 <span>/</span> 04</div><div class="hero-tag">✦ TUESDAY<br><strong>LIVE SESSION</strong></div><div class="hero-play">${icon('play', 22)}</div></div></section>
    <section class="stats-row" aria-label="Your progress"><div class="stat"><span class="stat-icon orange">↗</span><div><strong>7</strong><span>day streak</span></div><small>+2 this week</small></div><div class="stat"><span class="stat-icon blue">◒</span><div><strong>14.5</strong><span>hours this month</span></div><small>of 20 goal</small></div><div class="stat"><span class="stat-icon purple">✦</span><div><strong>82%</strong><span>weekly goal</span></div><small>Great pace!</small></div></section>
    <section class="section-block" id="saved"><div class="section-heading"><div><p class="eyebrow">CURATED FOR YOU</p><h2>Build your practice</h2></div><a class="view-all" href="#workouts">View all ${icon('arrow', 16)}</a></div><div class="filter-bar"><button class="filter active" data-filter="All">All workouts</button><button class="filter" data-filter="Strength">Strength</button><button class="filter" data-filter="Mobility">Mobility</button><button class="filter" data-filter="Cardio">Cardio</button></div><div class="workout-grid" id="workout-grid"></div></section>
    <section class="section-block lower-grid" id="schedule"><div><div class="section-heading compact"><div><p class="eyebrow">THIS WEEK</p><h2>Your rhythm</h2></div><a class="view-all" href="#schedule">See calendar ${icon('arrow', 16)}</a></div><div class="week-card"><div class="week-days"><span>MON<strong>22</strong><i class="done"></i></span><span class="today">TUE<strong>23</strong><i></i></span><span>WED<strong>24</strong><i></i></span><span>THU<strong>25</strong><i></i></span><span>FRI<strong>26</strong><i></i></span><span>SAT<strong>27</strong><i></i></span><span>SUN<strong>28</strong><i></i></span></div><div class="next-session"><div class="mini-image"></div><div><span class="eyebrow">UP NEXT · 06:30 PM</span><strong>Mobility reset</strong><small>18 min · Recovery</small></div><button class="outline-button" data-action="add-session">Add to calendar</button></div></div></div><div class="quote-card"><span class="quote-mark">“</span><blockquote>The body achieves what the mind believes.</blockquote><small>— Napoleon Hill</small><div class="quote-line"></div></div></section>
    <footer><span>© 2024 PULSE WELLNESS</span><span>Made for your best days.</span></footer>
  </main>
`

const grid = document.querySelector('#workout-grid')
let favorites = new Set()

function renderWorkouts(filter = 'All') {
  const visible = workouts.filter((workout) => filter === 'All' || workout.category === filter)
  grid.innerHTML = visible.map((workout) => `<article class="workout-card ${workout.accent}"><div class="workout-image" style="background-image: url('${workout.image}')"><button class="save-button ${favorites.has(workout.id) ? 'saved' : ''}" data-save="${workout.id}" aria-label="Save ${workout.title}">${icon('heart', 18)}</button><span class="duration">${workout.duration}</span></div><div class="workout-info"><div><span class="category">${workout.category}</span><h3>${workout.title}</h3><p>${workout.level}</p></div><button class="round-play" data-workout="${workout.id}" aria-label="Start ${workout.title}">${icon('play', 16)}</button></div></article>`).join('')
}

renderWorkouts()

document.addEventListener('click', (event) => {
  const filterButton = event.target.closest('[data-filter]')
  if (filterButton) {
    document.querySelectorAll('.filter').forEach((button) => button.classList.remove('active'))
    filterButton.classList.add('active')
    renderWorkouts(filterButton.dataset.filter)
  }
  const saveButton = event.target.closest('[data-save]')
  if (saveButton) {
    const id = saveButton.dataset.save
    favorites.has(id) ? favorites.delete(id) : favorites.add(id)
    renderWorkouts(document.querySelector('.filter.active').dataset.filter)
  }
  const action = event.target.closest('[data-action]')
  if (action) {
    action.classList.add('completed')
    action.innerHTML = `Session added ${icon('heart', 17)}`
  }
})
