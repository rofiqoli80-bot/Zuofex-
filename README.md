<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Zuofex 🍈 | Aesthetic Social</title>

    <script src="https://www.gstatic.com/firebasejs/10.8.1/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.1/firebase-auth-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.1/firebase-firestore-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.1/firebase-storage-compat.js"></script>

    <script>
        // For Firebase JS SDK v7.20.0 and later, measurementId is optional
const firebaseConfig = {
  apiKey: "AIzaSyAi68No6OrANo8Zvpsm84MaqyjXjmnje3A",
  authDomain: "suikaapp-84ed2.firebaseapp.com",
  projectId: "suikaapp-84ed2",
  storageBucket: "suikaapp-84ed2.firebasestorage.app",
  messagingSenderId: "346401107961",
  appId: "1:346401107961:web:225d2627d97fd478459728",
  measurementId: "G-NFTFSFX7Q5"
};
        firebase.initializeApp(firebaseConfig);
        window.firebaseAuth = firebase.auth();
        window.firebaseDb = firebase.firestore(); 
        window.firebaseStorage = firebase.storage(); 
        window.googleProvider = new firebase.auth.GoogleAuthProvider();
        
        window.firebaseSignIn = (authObj, providerObj) => authObj.signInWithPopup(providerObj);
        window.firebaseSignOut = (authObj) => authObj.signOut();
        window.firebaseOnAuth = (authObj, callback) => authObj.onAuthStateChanged(callback);
        
        console.log("Zuofex v1.0 Production Build Active! 🍈🚀");
    </script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@500;700&display=swap');

        :root {
            --bg-color: #fdf5f6; --primary: #ffb7c5; --primary-dark: #ff748f;
            --text-dark: #6d6875; --white: #ffffff;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Quicksand', sans-serif; }

        body {
            background-color: #ffe5ec; color: var(--text-dark);
            display: flex; justify-content: center; align-items: center;
            height: 100vh; overflow: hidden;
            background: linear-gradient(120deg, #ffe5ec, #ffc2d1, #ffe5ec);
            background-size: 200% 200%;
            animation: gradientBg 10s ease infinite;
        }

        @keyframes gradientBg { 0% { background-position: 0% 50%; } 50% { background-position: 100% 50%; } 100% { background-position: 0% 50%; } }

        #app-container {
            width: 100%; max-width: 450px; height: 100vh;
            background: rgba(253, 245, 246, 0.95); position: relative;
            overflow: hidden; box-shadow: 0 0 60px rgba(255, 183, 197, 0.6);
            display: flex; flex-direction: column; backdrop-filter: blur(10px);
        }

        .overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: rgba(253, 245, 246, 0.8); backdrop-filter: blur(15px); z-index: 9999; display: flex; flex-direction: column; justify-content: center; align-items: center; padding: 20px; text-align: center; }
        .hidden { display: none !important; }

        .glass-box { background: rgba(255, 255, 255, 0.95); padding: 30px; border-radius: 30px; border: 3px solid var(--white); box-shadow: 0 20px 40px rgba(255, 183, 197, 0.5); width: 90%; max-height: 85vh; overflow-y: auto; }
        .glass-box h2 { color: var(--primary-dark); margin-bottom: 15px; font-size: 1.8rem; }
        
        .btn { background: linear-gradient(135deg, #ff4d6d, #ff748f); color: white; border: none; padding: 15px 30px; font-size: 1.2rem; font-weight: 700; border-radius: 50px; cursor: pointer; transition: transform 0.2s, box-shadow 0.2s; width: 100%; margin-top: 15px; box-shadow: 0 8px 20px rgba(255, 77, 109, 0.3); }
        .btn:hover { transform: translateY(-2px); box-shadow: 0 12px 25px rgba(255, 77, 109, 0.4); }
        .btn:disabled { opacity: 0.7; cursor: not-allowed; transform: none; }

        .checkbox-container { display: flex; align-items: center; gap: 10px; margin: 20px 0; text-align: left; font-size: 0.9rem;}
        .checkbox-container a { color: var(--primary-dark); text-decoration: underline; cursor: pointer; }

        .view { width: 100%; height: calc(100% - 70px); overflow-y: auto; display: none; }
        .view.active { display: block; animation: fadeIn 0.3s ease; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        .bottom-nav { position: absolute; bottom: 0; width: 100%; height: 70px; background: rgba(255, 255, 255, 0.95); backdrop-filter: blur(15px); display: flex; justify-content: space-around; align-items: center; border-top: 1px solid rgba(255, 229, 236, 0.8); z-index: 1000; }
        .nav-item { font-size: 1.8rem; cursor: pointer; transition: 0.3s; filter: grayscale(100%); opacity: 0.5; position: relative;}
        .nav-item.active { filter: grayscale(0%); opacity: 1; transform: scale(1.15); }

        #feed-view { scroll-snap-type: y mandatory; overflow-y: scroll; padding: 0; scroll-behavior: smooth; background: #000; }
        #feed-view::-webkit-scrollbar { display: none; }
        
        .reel { width: 100%; height: 100%; scroll-snap-align: start; position: relative; background: #111; display: flex; justify-content: center; align-items: center; overflow: hidden; }
        .reel video { width: 100%; height: 100%; object-fit: cover; }
        
        .reel-actions { position: absolute; right: 15px; bottom: 90px; display: flex; flex-direction: column; gap: 20px; align-items: center; z-index: 10;}
        .action-btn { background: rgba(255, 255, 255, 0.2); backdrop-filter: blur(10px); width: 50px; height: 50px; border-radius: 50%; display: flex; justify-content: center; align-items: center; font-size: 1.5rem; color: white; cursor: pointer; border: 2px solid rgba(255,255,255,0.4); transition: 0.2s; flex-direction: column; position: relative; }
        .action-btn:active { transform: scale(0.9); }
        .action-btn.liked { background: rgba(255, 0, 0, 0.7); border-color: #ff4d6d; }
        .action-btn.saved { background: rgba(255, 183, 197, 0.9); border-color: #fff; }
        .action-label { font-size: 0.7rem; color: white; text-shadow: 0 1px 3px rgba(0,0,0,0.8); margin-top: 5px; font-weight: bold;}
        .like-count { position: absolute; bottom: -20px; font-size: 0.8rem; font-weight: bold; text-shadow: 0 1px 3px rgba(0,0,0,0.8); }
        
        .reel-info { position: absolute; left: 15px; bottom: 20px; color: white; text-shadow: 0 2px 5px rgba(0,0,0,0.9); width: 75%; z-index: 10;}
        .reel-info h3 { font-size: 1.2rem; margin-bottom: 5px; display: flex; align-items: center; gap: 8px;}
        .reel-info p { font-size: 0.95rem; line-height: 1.4; }
        .follow-badge { background: var(--primary-dark); color: white; border: none; padding: 4px 12px; border-radius: 15px; font-size: 0.75rem; cursor: pointer; font-weight: bold; transition: 0.2s;}
        .follow-badge.following { background: rgba(255,255,255,0.3); border: 1px solid white;}

        .about-slide { background: var(--bg-color) !important; flex-direction: column; text-align: center; padding: 20px;}
        .scene { width: 250px; height: 150px; perspective: 1000px; margin: 20px 0; }
        .logo-3d-card { width: 100%; height: 100%; background: rgba(255, 255, 255, 0.95); border-radius: 30px; box-shadow: 0 15px 35px rgba(255, 183, 197, 0.4); display: flex; flex-direction: column; align-items: center; justify-content: center; transform-style: preserve-3d; transition: transform 0.1s ease-out; border: 4px solid #fff; }
        .logo-text { font-size: 2.5rem; color: var(--primary); font-weight: 700; text-shadow: 0 5px 10px rgba(255, 183, 197, 0.5); transform: translateZ(50px); margin: 0; }
        .eyes { display: flex; gap: 15px; transform: translateZ(60px); margin-top: 5px;}
        .eye { width: 10px; height: 10px; background: #2b2d42; border-radius: 50%; }
        .mouth { width: 12px; height: 4px; background: #2b2d42; border-radius: 10px; transform: translateZ(60px); margin-top: 5px;}
        .about-slide h2 { color: var(--primary-dark); font-size: 1.8rem; }
        .about-slide p { color: var(--text-dark); font-weight: bold; margin-top: 15px; line-height: 1.5; }

        #profile-view { padding: 20px; background: rgba(255,255,255,0.7); }
        .profile-header { display: flex; flex-direction: column; align-items: center; margin-bottom: 20px; text-align: center;}
        .avatar-wrap { position: relative; margin-bottom: 10px; }
        .avatar { font-size: 3.5rem; background: var(--bg-color); border-radius: 50%; width: 90px; height: 90px; display: flex; justify-content: center; align-items: center; border: 3px solid var(--primary); box-shadow: 0 10px 20px rgba(255, 183, 197, 0.4);}
        .name-edit { font-size: 1.5rem; font-weight: 700; color: var(--text-dark); display: flex; align-items: center; gap: 10px; }
        .zuofex-id { background: var(--primary); color: white; padding: 4px 12px; border-radius: 15px; font-size: 0.85rem; font-weight: bold; margin-top: 8px; letter-spacing: 1px; box-shadow: 0 5px 10px rgba(255, 183, 197, 0.3);}
        .stats { display: flex; gap: 30px; margin-top: 20px; width: 100%; justify-content: center; border-bottom: 2px dashed #ffc2d1; padding-bottom: 20px;}
        .stat { text-align: center; cursor: pointer; }
        .stat span { display: block; font-weight: bold; font-size: 1.4rem; color: var(--primary-dark); }
        
        .profile-tabs { display: flex; width: 100%; margin-top: 10px; border-bottom: 2px solid #ffc2d1; }
        .p-tab { flex: 1; text-align: center; padding: 10px; font-weight: bold; cursor: pointer; color: #aaa; transition: 0.3s;}
        .p-tab.active { color: var(--primary-dark); border-bottom: 3px solid var(--primary-dark); }

        .grid-gallery { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 3px; margin-top: 5px; width: 100%;}
        .grid-item { background: #eee; aspect-ratio: 9/16; position: relative; cursor: pointer; overflow: hidden; border-radius: 5px;}
        .grid-item video { width: 100%; height: 100%; object-fit: cover; }
        .grid-icon { position: absolute; top: 5px; right: 5px; color: white; font-size: 1rem; text-shadow: 0 1px 3px rgba(0,0,0,0.8); }

        #post-viewer-overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: #000; z-index: 10000; display: flex; flex-direction: column; }
        .viewer-header { position: absolute; top: 0; width: 100%; padding: 20px; display: flex; justify-content: space-between; align-items: center; z-index: 10; background: linear-gradient(to bottom, rgba(0,0,0,0.7), transparent); }
        .close-btn { color: white; font-size: 2rem; cursor: pointer; text-shadow: 0 2px 4px rgba(0,0,0,0.5); }
        .delete-btn { background: #ff4d6d; color: white; border: none; padding: 8px 15px; border-radius: 20px; font-weight: bold; cursor: pointer; display: none;}
        #viewer-video { width: 100%; height: 100%; object-fit: cover; }

        #upload-view { padding: 30px; text-align: center; background: rgba(255,255,255,0.7); flex-direction: column; justify-content: center; height: calc(100% - 70px); display: none;}
        #upload-view.active { display: flex; }
        
        .upload-area { border: 3px dashed var(--primary-dark); padding: 50px 20px; border-radius: 30px; margin-bottom: 20px; background: rgba(255,255,255,0.9); cursor: pointer; transition: 0.2s;}
        .upload-area:hover { background: #ffe5ec; border-color: var(--primary); }
        .caption-input { width: 100%; padding: 15px; border: 2px solid var(--primary); border-radius: 15px; margin-bottom: 20px; font-family: inherit; outline: none; font-size: 1rem; background: rgba(255,255,255,0.9);}
        #upload-preview { width: 100%; max-height: 250px; border-radius: 15px; display: none; object-fit: cover; margin-bottom: 15px; border: 2px solid var(--primary); box-shadow: 0 10px 20px rgba(0,0,0,0.1);}

        #chat-view { padding: 0; background: rgba(255,255,255,0.7); flex-direction: column; display: none; }
        #chat-view.active { display: flex; }
        
        .chat-header { padding: 20px; background: rgba(253, 245, 246, 0.9); border-bottom: 2px solid #ffc2d1;}
        .search-bar { display: flex; gap: 10px; margin-top: 15px;}
        .search-bar input { flex: 1; padding: 12px 20px; border: 2px solid var(--primary); border-radius: 25px; outline: none; font-family: inherit; font-size: 0.95rem;}
        
        .chat-list { flex: 1; overflow-y: auto; padding: 10px; }
        .friend-item { display: flex; align-items: center; justify-content: space-between; padding: 15px; background: rgba(255,255,255,0.9); border-radius: 20px; margin-bottom: 10px; border: 1px solid #ffe5ec; cursor: pointer; transition: 0.2s; box-shadow: 0 4px 10px rgba(255, 183, 197, 0.1);}
        .friend-item:hover { background: #fff0f3; transform: translateY(-2px); box-shadow: 0 6px 15px rgba(255, 183, 197, 0.3);}
        .friend-info { display: flex; align-items: center; gap: 15px; }
        .f-avatar { font-size: 2.2rem; background: #ffe5ec; width: 50px; height: 50px; border-radius: 50%; display: flex; justify-content: center; align-items: center; border: 2px solid white;}
        .f-details h4 { color: var(--text-dark); margin-bottom: 3px;}
        .f-details p { font-size: 0.8rem; color: #999; }
        
        #dm-view { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: var(--bg-color); z-index: 10001; display: flex; flex-direction: column; transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1); transform: translateX(100%); }
        #dm-view.open { transform: translateX(0); }
        .dm-header { display: flex; align-items: center; padding: 15px 20px; background: rgba(255,255,255,0.95); box-shadow: 0 4px 15px rgba(255, 183, 197, 0.2); gap: 15px; border-bottom: 1px solid #ffe5ec;}
        .dm-back { font-size: 1.5rem; cursor: pointer; color: var(--primary-dark); transition: 0.2s;}
        .dm-back:active { transform: scale(0.8); }
        .dm-messages { flex: 1; overflow-y: auto; padding: 20px; display: flex; flex-direction: column; gap: 15px; background: url('https://www.transparenttextures.com/patterns/cubes.png');}
        .msg-bubble { max-width: 75%; padding: 12px 18px; border-radius: 20px; font-size: 0.95rem; line-height: 1.4; position: relative; box-shadow: 0 2px 5px rgba(0,0,0,0.05);}
        .msg-received { background: var(--white); align-self: flex-start; border-bottom-left-radius: 5px; border: 1px solid #ffe5ec;}
        .msg-sent { background: var(--primary-dark); color: white; align-self: flex-end; border-bottom-right-radius: 5px; }
        .msg-sender-name { font-size: 0.7rem; opacity: 0.7; margin-bottom: 4px; display: block; font-weight: bold; }
        
        .shared-vid-card { width: 200px; border-radius: 15px; overflow: hidden; margin-top: 5px; border: 2px solid rgba(255,255,255,0.5); cursor: pointer; position: relative;}
        .shared-vid-card video { width: 100%; display: block; }
        .shared-vid-card::after { content: '▶'; position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); color: white; font-size: 2rem; text-shadow: 0 2px 5px rgba(0,0,0,0.5); pointer-events: none;}

        .dm-input-area { padding: 15px; background: rgba(255,255,255,0.95); display: flex; gap: 10px; align-items: center; border-top: 1px solid #ffe5ec; }
        .dm-input-area input { flex: 1; padding: 12px 20px; border: 1px solid #ffe5ec; background: var(--bg-color); border-radius: 25px; outline: none; font-family: inherit;}
        .send-btn { background: var(--primary-dark); color: white; border: none; width: 40px; height: 40px; border-radius: 50%; cursor: pointer; display: flex; justify-content: center; align-items: center; font-size: 1.2rem; transition: 0.2s; box-shadow: 0 4px 10px rgba(255, 77, 109, 0.3);}
        .send-btn:active { transform: scale(0.9); }

        #comments-overlay { justify-content: flex-end; padding: 0; background: rgba(0,0,0,0.5); z-index: 10002; transition: opacity 0.3s; }
        .comments-box { background: var(--white); width: 100%; height: 65vh; border-radius: 30px 30px 0 0; padding: 20px; display: flex; flex-direction: column; box-shadow: 0 -10px 40px rgba(0,0,0,0.2); transform: translateY(100%); transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275); }
        #comments-overlay.open .comments-box { transform: translateY(0); }
        .comment-item { display: flex; gap: 12px; margin-bottom: 15px; }
        .comment-avatar { background: #ffe5ec; width: 35px; height: 35px; border-radius: 50%; display: flex; justify-content: center; align-items: center; font-size: 1.2rem; flex-shrink: 0; border: 1px solid var(--primary);}
        .comment-content h5 { font-size: 0.85rem; color: #999; margin-bottom: 2px; }
        .comment-content p { font-size: 0.95rem; color: var(--text-dark); line-height: 1.3; }

        .loading-spinner { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); font-size: 2rem; animation: spin 2s infinite linear; color: #ff748f; z-index: 10; display: none; }
        @keyframes spin { 100% { transform: translate(-50%, -50%) rotate(360deg); } }
    </style>
</head>
<body class="locked">
<div id="app-container">

    <div id="cookie-overlay" class="overlay">
        <div class="glass-box">
            <h2>Welcome to Zuofex 🍈</h2>
            <p>We use cookies 🍪 to ensure you get the best aesthetic experience.</p>
            <button class="btn" id="btn-accept-cookies">Enter</button>
        </div>
    </div>

    <div id="login-overlay" class="overlay hidden">
        <div class="glass-box">
            <h2>Zuofex ID Login</h2>
            <p style="font-size: 0.9rem;">Join the digital aesthetic space.</p>
            <div class="checkbox-container">
                <input type="checkbox" id="tnc-checkbox">
                <label for="tnc-checkbox">I accept the <a id="link-tnc">Terms & Conditions</a></label>
            </div>
            <button class="btn" id="btn-zuofex-login" style="background: #2b2d42; color: white; display: flex; justify-content: center; align-items: center; gap: 10px;">
                <span style="font-size: 1.5rem;">🍈</span> Secure Login
            </button>
        </div>
    </div>

    <div id="tnc-overlay" class="overlay hidden" style="z-index: 99999;">
        <div class="glass-box" style="max-height: 80%; overflow-y: auto;">
            <h2>Terms & Conditions</h2>
            <p>1. Keep the aesthetic pure.</p>
            <p>2. Be kind in chats.</p>
            <p>3. Uploaded videos belong to you.</p>
            <p>Copyright © 2026 Zuofex. All rights reserved.</p>
            <button class="btn" id="btn-close-tnc" style="margin-top: 30px;">Close & Agree</button>
        </div>
    </div>

    <div id="main-app" class="hidden" style="height: 100%; width: 100%;">
        
        <div id="feed-view" class="view active">
            <div class="loading-spinner" id="feed-spinner">✨</div>
            <div class="reel about-slide">
                <div class="scene">
                    <div class="logo-3d-card" id="logoCard">
                        <h1 class="logo-text">Zuofex</h1>
                        <div class="eyes"><div class="eye"></div><div class="eye"></div></div>
                        <div class="mouth"></div>
                    </div>
                </div>
                <h2 style="color: var(--primary-dark);">Welcome ✨</h2>
                <p style="margin-top: 15px; font-weight: bold; width: 85%;">Your digital workspace and aesthetic discovery engine. Connect, share, and find your vibe.</p>
                <p style="margin-top: 10px; font-size: 0.9rem; color: var(--primary-dark);">👇 Swipe up to explore</p>
            </div>
        </div>

        <div id="chat-view" class="view">
            <div class="chat-header">
                <h2 style="color: var(--primary-dark);">Discover & Chat 💬</h2>
                <div class="search-bar">
                    <input type="text" id="search-input" placeholder="Search Live DB by ZF-ID...">
                    <button class="btn" id="btn-search" style="width: auto; margin:0; padding: 0 20px;">🔍</button>
                </div>
            </div>
            <div class="chat-list" id="chat-list">
                <div class="friend-item open-dm" data-name="Global Lounge" data-id="global-room" data-avatar="🌍">
                    <div class="friend-info">
                        <div class="f-avatar">🌍</div>
                        <div class="f-details">
                            <h4>Global Lounge</h4>
                            <p>Public Room • Tap to chat</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div id="upload-view" class="view">
            <h2 style="color: var(--primary-dark); margin-bottom: 20px;">Post to Zuofex 🎬</h2>
            <label for="video-upload" class="upload-area" id="upload-label">
                <h1 style="font-size: 3rem;" id="upload-icon">📁</h1>
                <p id="upload-text">Tap to select video from Gallery</p>
            </label>
            <input type="file" id="video-upload" accept="video/*" class="hidden">
            <video id="upload-preview" controls loop playsinline></video>
            <input type="text" id="caption-input" class="caption-input" placeholder="Write an aesthetic caption...">
            <button class="btn" id="btn-post-video">Post Video</button>
        </div>

        <div id="profile-view" class="view">
            <div class="profile-header">
                <div class="avatar-wrap">
                    <div class="avatar" id="profile-avatar">🍈</div>
                </div>
                <div class="name-edit" id="profile-name-display">User <span style="font-size: 1rem; cursor: pointer;" id="btn-edit-name">✏️</span></div>
                <div class="zuofex-id" id="profile-id-display">ZF-00000</div>
                <div class="stats">
                    <div class="stat"><span id="following-count">0</span> Following</div>
                    <div class="stat"><span id="follower-count">0</span> Followers</div>
                    <div class="stat"><span id="saved-count">0</span> Saved</div>
                </div>
                <button class="btn" id="btn-logout" style="padding: 10px 20px; font-size: 1rem; margin-top: 15px; width: 60%; background: #ddd; color: #333; box-shadow: none;">Log Out</button>
            </div>
            <div class="profile-tabs">
                <div class="p-tab active" id="tab-saved">Saved 🔖</div>
                <div class="p-tab" id="tab-uploads">Uploads 🎬</div>
            </div>
            <div class="grid-gallery" id="profile-gallery"></div>
        </div>

        <div class="bottom-nav">
            <div class="nav-item active" data-target="feed-view">🏠</div>
            <div class="nav-item" data-target="chat-view">💬</div>
            <div class="nav-item" data-target="upload-view">➕</div>
            <div class="nav-item" data-target="profile-view">👤</div>
        </div>
        
        <div id="dm-view">
            <div class="dm-header">
                <div class="dm-back" id="dm-back-btn">⬅️</div>
                <div class="f-avatar" id="dm-avatar" style="width: 40px; height: 40px; font-size: 1.5rem;">🌍</div>
                <h3 id="dm-name" style="color: var(--text-dark);">Name</h3>
            </div>
            <div class="dm-messages" id="dm-messages"></div>
            <div class="dm-input-area">
                <input type="text" id="dm-input" placeholder="Type a message...">
                <button class="send-btn" id="btn-send-dm">➤</button>
            </div>
        </div>

        <div id="post-viewer-overlay" class="hidden">
            <div class="viewer-header">
                <div class="close-btn" id="close-viewer">✖</div>
                <button class="delete-btn" id="delete-post-btn">Delete</button>
            </div>
            <video id="viewer-video" controls autoplay loop playsinline></video>
        </div>

        <div id="comments-overlay" class="overlay hidden">
            <div class="comments-box">
                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px;">
                    <h3 style="color: var(--primary-dark);">Comments 💬</h3>
                    <div id="close-comments" style="font-size: 1.5rem; cursor: pointer;">✖</div>
                </div>
                <div id="comments-list" style="flex: 1; overflow-y: auto; text-align: left; padding-right: 5px;"></div>
                <div class="dm-input-area" style="padding: 10px 0 0 0; border: none; background: transparent;">
                    <input type="text" id="comment-input" placeholder="Add a comment..." style="background: #fdf5f6; border: 1px solid #ffe5ec;">
                    <button class="send-btn" id="btn-send-comment">➤</button>
                </div>
            </div>
        </div>
    </div> 
</div> 

<script>
    const PEXELS_API_KEY = "PUT_YOUR_PEXELS_API_KEY_HERE"; 
    
    let currentUser = { uid: "", id: "", name: "Aesthetic User", avatar: "🍈", saved: [], uploads: [], followers: [], following: [] };
    let isLoadingFeed = false; let currentPage = 1; let currentProfileTab = 'saved'; let currentViewerVideoUrl = null; let isFirebaseReady = false;
    let currentChatId = null; let chatUnsubscribe = null; 
    let currentCommentPostId = null; let commentsUnsubscribe = null;

    async function syncUserWithDatabase(googleUser) {
        try {
            const userRef = window.firebaseDb.collection('users').doc(googleUser.uid);
            const doc = await userRef.get();
            if (!doc.exists) {
                const newUserData = {
                    uid: googleUser.uid, id: "ZF-" + Math.floor(10000 + Math.random() * 90000), name: googleUser.displayName || "Aesthetic User",
                    avatar: "🍈", saved: [], uploads: [], followers: [], following: [], createdAt: firebase.firestore.FieldValue.serverTimestamp()
                };
                await userRef.set(newUserData); currentUser = newUserData;
            } else {
                currentUser = doc.data();
                if(!currentUser.saved) currentUser.saved = []; if(!currentUser.uploads) currentUser.uploads = [];
                if(!currentUser.followers) currentUser.followers = []; if(!currentUser.following) currentUser.following = [];
            }
        } catch (error) {
            currentUser.uid = googleUser.uid || "local_test_uid"; currentUser.id = "ZF-" + Math.floor(10000 + Math.random() * 90000);
            currentUser.name = googleUser.displayName || "Aesthetic User";
        }
    }

    window.firebaseOnAuth(window.firebaseAuth, async (user) => { if (user) { await syncUserWithDatabase(user); isFirebaseReady = true; } });

    document.getElementById('btn-accept-cookies').addEventListener('click', () => {
        document.getElementById('cookie-overlay').classList.add('hidden');
        if (isFirebaseReady) { document.getElementById('main-app').classList.remove('hidden'); updateProfileUI(); startGlobalFeed(); } 
        else { document.getElementById('login-overlay').classList.remove('hidden'); }
    });

    document.getElementById('link-tnc').addEventListener('click', () => document.getElementById('tnc-overlay').classList.remove('hidden'));
    document.getElementById('btn-close-tnc').addEventListener('click', () => { document.getElementById('tnc-overlay').classList.add('hidden'); document.getElementById('tnc-checkbox').checked = true; });

    document.getElementById('btn-zuofex-login').addEventListener('click', async () => {
        if(!document.getElementById('tnc-checkbox').checked) return alert("Please accept the Terms & Conditions first! ✨");
        try {
            const result = await window.firebaseSignIn(window.firebaseAuth, window.googleProvider);
            await syncUserWithDatabase(result.user);
            document.getElementById('login-overlay').classList.add('hidden'); document.getElementById('main-app').classList.remove('hidden');
            updateProfileUI(); startGlobalFeed();
        } catch (error) {
            currentUser.id = "ZF-" + Math.floor(10000 + Math.random() * 90000); currentUser.uid = "local_" + currentUser.id;
            document.getElementById('login-overlay').classList.add('hidden'); document.getElementById('main-app').classList.remove('hidden');
            updateProfileUI(); startGlobalFeed();
        }
    });

    document.getElementById('btn-logout').addEventListener('click', () => { window.firebaseSignOut(window.firebaseAuth).then(() => location.reload()); });

    document.querySelectorAll('.nav-item').forEach(item => {
        item.addEventListener('click', function() {
            const targetId = this.getAttribute('data-target');
            document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active')); this.classList.add('active');
            document.querySelectorAll('.view').forEach(v => v.classList.remove('active')); document.getElementById(targetId).classList.add('active');
            if (targetId !== 'feed-view') document.querySelectorAll('#feed-view video').forEach(v => v.pause()); else handleVideoVisibility();
        });
    });

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                let playPromise = entry.target.play(); if (playPromise !== undefined) playPromise.catch(e => {});
                const reels = document.querySelectorAll('.reel');
                if (Array.from(reels).indexOf(entry.target.parentElement) >= reels.length - 2) fetchReels();
            } else { entry.target.pause(); }
        });
    }, { threshold: 0.6 });

    async function startGlobalFeed() {
        if (isLoadingFeed) return; isLoadingFeed = true; document.getElementById('feed-spinner').style.display = "block";
        try {
            const postsSnapshot = await window.firebaseDb.collection('posts').orderBy('createdAt', 'desc').limit(5).get();
            if (!postsSnapshot.empty) postsSnapshot.forEach(doc => {
                const post = doc.data();
                createReel(post.videoUrl, post.caption, post.authorName, false, doc.id, post.likes || [], post.authorUid);
            });
        } catch (error) {}
        isLoadingFeed = false; await fetchReels(); 
    }

    async function fetchReels() {
        if (isLoadingFeed) return; isLoadingFeed = true; document.getElementById('feed-spinner').style.display = "block";
        if (PEXELS_API_KEY.includes("PUT_YOUR") || PEXELS_API_KEY.length < 50) { isLoadingFeed = false; document.getElementById('feed-spinner').style.display = "none"; return; }
        try {
            const res = await fetch(`https://api.pexels.com/videos/search?query=aesthetic+relaxing&orientation=portrait&per_page=3&page=${currentPage}`, { headers: { Authorization: PEXELS_API_KEY } });
            const data = await res.json();
            if (data.videos && data.videos.length > 0) {
                data.videos.forEach(vid => {
                    const link = vid.video_files.find(f => f.quality === 'hd')?.link || vid.video_files[0].link;
                    createReel(link, "Pexels Aesthetic ✨", vid.user.name, false, null, [], null);
                });currentPage++;
            } else { currentPage = 1; }
        } catch(e) {} finally { isLoadingFeed = false; document.getElementById('feed-spinner').style.display = "none"; }
    }

    function createReel(url, caption, author, prepend = false, postId = null, likes = [], authorUid = null) {
        const feed = document.getElementById('feed-view');
        const reel = document.createElement('div'); reel.className = 'reel';
        
        const hasLiked = currentUser.uid && likes.includes(currentUser.uid);
        const isFollowing = currentUser.uid && authorUid && currentUser.following.includes(authorUid);
        
        const likeIcon = hasLiked ? '❤️' : '🤍'; const likeClass = hasLiked ? 'liked' : ''; const numLikes = likes.length;
        const followText = isFollowing ? 'Following' : 'Follow'; const followClass = isFollowing ? 'following' : '';
        const followBtnHtml = (authorUid === currentUser.uid) ? '' : `<button class="follow-badge ${followClass}">${followText}</button>`;
        
        reel.innerHTML = `
            <video src="${url}" loop playsinline preload="metadata"></video>
            <div class="reel-actions">
                <div class="action-btn btn-like ${likeClass}"><span style="font-size:1.2rem;">${likeIcon}</span><div class="like-count">${numLikes > 0 ? numLikes : ''}</div><div class="action-label">Like</div></div>
                <div class="action-btn btn-chat"><span style="font-size:1.2rem;">💬</span><div class="action-label">Comment</div></div>
                <div class="action-btn btn-share"><span style="font-size:1.2rem;">📤</span><div class="action-label">Share</div></div>
                <div class="action-btn btn-save" data-url="${url}"><span style="font-size:1.2rem;">🔖</span><div class="action-label">Save</div></div>
            </div>
            <div class="reel-info">
                <h3>👤 ${author} ${followBtnHtml}</h3>
                <p>${caption} #zuofex</p>
            </div>
        `;

        reel.querySelector('.btn-like').addEventListener('click', async function() {
            if (!currentUser.uid || currentUser.uid.includes("local")) return alert("Login required! ✨");
            const isCurrentlyLiked = this.classList.contains('liked');
            this.classList.toggle('liked'); this.querySelector('span').innerText = isCurrentlyLiked ? '🤍' : '❤️';
            if (postId) {
                const postRef = window.firebaseDb.collection('posts').doc(postId);
                try {
                    if (isCurrentlyLiked) {
                        await postRef.update({ likes: firebase.firestore.FieldValue.arrayRemove(currentUser.uid) });
                        this.querySelector('.like-count').innerText = (numLikes - 1) > 0 ? (numLikes - 1) : '';
                    } else {
                        await postRef.update({ likes: firebase.firestore.FieldValue.arrayUnion(currentUser.uid) });
                        this.querySelector('.like-count').innerText = numLikes + 1;
                    }
                } catch(e) {}
            } else { this.querySelector('.like-count').innerText = isCurrentlyLiked ? '' : '1'; }
        });

        const followBtn = reel.querySelector('.follow-badge');
        if (followBtn) {
            followBtn.addEventListener('click', async function() {
                if (!currentUser.uid || currentUser.uid.includes("local")) return alert("Login required to follow! ✨");
                if (!authorUid) return alert("Pexels creators cannot be followed yet! ✨");
                const currentlyFollowing = this.classList.contains('following');
                this.classList.toggle('following'); this.innerText = currentlyFollowing ? 'Follow' : 'Following';
                try {
                    const myRef = window.firebaseDb.collection('users').doc(currentUser.uid);
                    const authorRef = window.firebaseDb.collection('users').doc(authorUid);
                    if (currentlyFollowing) {
                        currentUser.following = currentUser.following.filter(id => id !== authorUid);
                        await myRef.update({ following: firebase.firestore.FieldValue.arrayRemove(authorUid) });
                        await authorRef.update({ followers: firebase.firestore.FieldValue.arrayRemove(currentUser.uid) });
                    } else {
                        currentUser.following.push(authorUid);
                        await myRef.update({ following: firebase.firestore.FieldValue.arrayUnion(authorUid) });
                        await authorRef.update({ followers: firebase.firestore.FieldValue.arrayUnion(currentUser.uid) });
                    }
                    updateProfileUI(); 
                } catch(e) {}
            });
        }

        reel.querySelector('.btn-chat').addEventListener('click', () => { if (postId) openCommentsModal(postId); else alert("Comments are only available on real Zuofex uploads! ✨"); });
        reel.querySelector('.btn-save').addEventListener('click', async function() {
            const vidUrl = this.getAttribute('data-url');
            if(!currentUser.saved.includes(vidUrl)) {
                currentUser.saved.push(vidUrl); this.classList.add('saved'); this.querySelector('span').innerText = '✅'; updateProfileGallery();
                if(currentUser.uid) await window.firebaseDb.collection('users').doc(currentUser.uid).update({ saved: currentUser.saved }).catch(()=>{});
            }
        });
        reel.querySelector('.btn-share').addEventListener('click', () => { document.querySelector('.nav-item[data-target="chat-view"]').click(); setTimeout(() => { document.querySelector('[data-id="global-room"]').click(); shareVideoToLiveChat(url); }, 500); });
        
        if (prepend) document.querySelector('.about-slide').insertAdjacentElement('afterend', reel); else feed.appendChild(reel);
        observer.observe(reel.querySelector('video'));
    }

    function handleVideoVisibility() { document.querySelectorAll('#feed-view video').forEach(v => { const rect = v.getBoundingClientRect(); if(rect.top >= 0 && rect.bottom <= window.innerHeight) { let playPromise = v.play(); if (playPromise !== undefined) playPromise.catch(e => {}); } }); }
    
    const card = document.getElementById('logoCard'); const scene = document.querySelector('.scene');
    scene.addEventListener('mousemove', (e) => { const rect = scene.getBoundingClientRect(); card.style.transform = `rotateX(${-(e.clientY - rect.top - rect.height / 2) / 10}deg) rotateY(${(e.clientX - rect.left - rect.width / 2) / 10}deg)`; });
    scene.addEventListener('mouseleave', () => card.style.transform = 'rotateX(0deg) rotateY(0deg)');

    function updateProfileUI() {
        document.getElementById('profile-name-display').innerHTML = `${currentUser.name} <span style="font-size: 1rem; cursor: pointer;" id="btn-edit-name">✏️</span>`;
        document.getElementById('profile-id-display').innerText = currentUser.id;
        document.getElementById('saved-count').innerText = currentUser.saved.length;
        document.getElementById('following-count').innerText = currentUser.following ? currentUser.following.length : 0;
        document.getElementById('follower-count').innerText = currentUser.followers ? currentUser.followers.length : 0;
        
        const editBtn = document.getElementById('btn-edit-name'); editBtn.replaceWith(editBtn.cloneNode(true));
        document.getElementById('btn-edit-name').addEventListener('click', async () => {
            const newName = prompt("Enter your new aesthetic name:");
            if(newName) { currentUser.name = newName; updateProfileUI(); if(currentUser.uid) await window.firebaseDb.collection('users').doc(currentUser.uid).update({ name: newName }).catch(()=>{}); }
        });
    }

    document.getElementById('tab-saved').addEventListener('click', function() { this.classList.add('active'); document.getElementById('tab-uploads').classList.remove('active'); currentProfileTab = 'saved'; updateProfileGallery(); });
    document.getElementById('tab-uploads').addEventListener('click', function() { this.classList.add('active'); document.getElementById('tab-saved').classList.remove('active'); currentProfileTab = 'uploads'; updateProfileGallery(); });

    function updateProfileGallery() {
        const gal = document.getElementById('profile-gallery'); document.getElementById('saved-count').innerText = currentUser.saved.length; gal.innerHTML = '';
        const dataArray = currentProfileTab === 'saved' ? currentUser.saved : currentUser.uploads; const icon = currentProfileTab === 'saved' ? '🔖' : '🎬';
        dataArray.forEach(url => {
            const item = document.createElement('div'); item.className = 'grid-item'; item.innerHTML = `<video src="${url}" muted preload="metadata"></video><div class="grid-icon">${icon}</div>`;
            item.addEventListener('click', () => openPostViewer(url, currentProfileTab === 'uploads')); gal.appendChild(item);
        });
    }

    let tempUploadUrl = null; let tempUploadFile = null; 
    const uploadInput = document.getElementById('video-upload'); const uploadPreview = document.getElementById('upload-preview');
    uploadInput.addEventListener('change', function(e) {
        if(e.target.files[0]) {
            tempUploadFile = e.target.files[0]; tempUploadUrl = URL.createObjectURL(tempUploadFile);
            document.getElementById('upload-icon').style.display = "none"; document.getElementById('upload-text').innerText = "Video Selected!";
            uploadPreview.style.display = "block"; uploadPreview.src = tempUploadUrl; uploadPreview.play();
        }
    });

    document.getElementById('btn-post-video').addEventListener('click', async () => {
        const caption = document.getElementById('caption-input').value || "My Aesthetic Upload ✨"; const postBtn = document.getElementById('btn-post-video');
        if(tempUploadFile) {
            postBtn.innerText = "Uploading to Cloud... ⏳"; postBtn.disabled = true;
            try {
                let finalVideoUrl = tempUploadUrl; let newPostId = null;
                if (currentUser.uid && !currentUser.uid.includes("local")) {
                    const videoRef = window.firebaseStorage.ref().child(`videos/${currentUser.uid}_${Date.now()}.mp4`);
                    await videoRef.put(tempUploadFile); finalVideoUrl = await videoRef.getDownloadURL();
                    const postRef = await window.firebaseDb.collection('posts').add({
                        authorUid: currentUser.uid, authorName: currentUser.name, videoUrl: finalVideoUrl, caption: caption, likes: [], createdAt: firebase.firestore.FieldValue.serverTimestamp()
                    });
                    newPostId = postRef.id; currentUser.uploads.push(finalVideoUrl);
                    await window.firebaseDb.collection('users').doc(currentUser.uid).update({ uploads: currentUser.uploads });
                }
                updateProfileGallery(); createReel(finalVideoUrl, caption, currentUser.name, true, newPostId, [], currentUser.uid);
                alert("Upload Complete! 🌍 Your video is now live."); document.querySelector('.nav-item[data-target="feed-view"]').click();
            } catch(e) { alert("Upload failed! Ensure Firebase Storage Rules allow writes."); } 
            finally {
                tempUploadFile = null; tempUploadUrl = null; uploadInput.value = ""; document.getElementById('upload-icon').style.display = "block";
                document.getElementById('upload-text').innerText = "Tap to select video from Gallery"; uploadPreview.style.display = "none"; uploadPreview.src = "";
                document.getElementById('caption-input').value = ''; postBtn.innerText = "Post Video"; postBtn.disabled = false;
            }
        } else { alert("Please select a video file first!"); }
    });

    const viewer = document.getElementById('post-viewer-overlay'); const viewerVideo = document.getElementById('viewer-video'); const deleteBtn = document.getElementById('delete-post-btn');
    function openPostViewer(url, isOwner) { currentViewerVideoUrl = url; viewer.classList.remove('hidden'); viewerVideo.src = url; viewerVideo.play(); deleteBtn.style.display = isOwner ? 'block' : 'none'; }
    document.getElementById('close-viewer').addEventListener('click', () => { viewer.classList.add('hidden'); viewerVideo.pause(); viewerVideo.src = ""; });
    deleteBtn.addEventListener('click', async () => {
        if(confirm("Are you sure you want to delete this upload?")) {
            currentUser.uploads = currentUser.uploads.filter(u => u !== currentViewerVideoUrl);
            document.querySelectorAll('#feed-view video').forEach(v => { if (v.src === currentViewerVideoUrl) v.parentElement.remove(); });
            viewer.classList.add('hidden'); viewerVideo.pause(); updateProfileGallery();
            if (currentUser.uid) await window.firebaseDb.collection('users').doc(currentUser.uid).update({ uploads: currentUser.uploads }).catch(()=>{});
        }
    });

    const searchInput = document.getElementById('search-input');
    document.getElementById('btn-search').addEventListener('click', async () => {
        const query = searchInput.value.trim().toUpperCase(); if (query === "") return;
        let localMatchFound = false;
        document.querySelectorAll('.friend-item').forEach(item => {
            const id = item.getAttribute('data-id').toUpperCase();
            if(id.includes(query)) { item.style.display = 'flex'; localMatchFound = true; } else { item.style.display = 'none'; }
        });
        if (query.startsWith("ZF-")) {
            document.getElementById('btn-search').innerText = "⏳";
            try {
                const snapshot = await window.firebaseDb.collection('users').where('id', '==', query).get();
                if (!snapshot.empty) {
                    snapshot.forEach(doc => {
                        const foundUser = doc.data();
                        if(!document.querySelector(`[data-id="${foundUser.uid}"]`)) {
                            const chatList = document.getElementById('chat-list'); const newItem = document.createElement('div');
                            newItem.className = 'friend-item open-dm'; newItem.setAttribute('data-name', foundUser.name); newItem.setAttribute('data-id', foundUser.uid); newItem.setAttribute('data-avatar', foundUser.avatar || '🌸');
                            newItem.innerHTML = `<div class="friend-info"><div class="f-avatar">${foundUser.avatar || '🌸'}</div><div class="f-details"><h4>${foundUser.name}</h4><p>${foundUser.id} • New Discovery!</p></div></div>`;
                            newItem.addEventListener('click', function() { document.getElementById('dm-name').innerText = this.getAttribute('data-name'); document.getElementById('dm-avatar').innerText = this.getAttribute('data-avatar'); dmView.classList.add('open'); startLiveChat(generateChatId(currentUser.uid, foundUser.uid)); });
                            chatList.appendChild(newItem); newItem.style.display = 'flex';
                        }
                    });
                } else if (!localMatchFound) { alert("No user found with that ZF-ID! ✨"); }
            } catch(e) {} finally { document.getElementById('btn-search').innerText = "🔍"; }
        }
    });
function generateChatId(uid1, uid2) { return uid1 < uid2 ? `${uid1}_${uid2}` : `${uid2}_${uid1}`; }
    const dmView = document.getElementById('dm-view'); const dmMessages = document.getElementById('dm-messages');
    document.querySelectorAll('.open-dm').forEach(item => {
        item.addEventListener('click', function() {
            document.getElementById('dm-name').innerText = this.getAttribute('data-name'); document.getElementById('dm-avatar').innerText = this.getAttribute('data-avatar'); dmView.classList.add('open'); startLiveChat(this.getAttribute('data-id')); 
        });
    });
    document.getElementById('dm-back-btn').addEventListener('click', () => { dmView.classList.remove('open'); if(chatUnsubscribe) chatUnsubscribe(); });

    function startLiveChat(chatId) {
        currentChatId = chatId; dmMessages.innerHTML = '<div style="text-align:center; padding: 20px; color:#aaa;">Loading live chat... ✨</div>';
        if(chatUnsubscribe) chatUnsubscribe(); 
        try {
            chatUnsubscribe = window.firebaseDb.collection('chats').doc(chatId).collection('messages').orderBy('timestamp', 'asc').onSnapshot(snapshot => {
                dmMessages.innerHTML = ''; 
                if (snapshot.empty) { dmMessages.innerHTML = '<div style="text-align:center; padding: 20px; color:#aaa;">No messages yet. Say hi! ✨</div>'; return; }
                snapshot.forEach(doc => {
                    const msg = doc.data(); const div = document.createElement('div'); const isMe = msg.senderId === currentUser.id; 
                    div.className = `msg-bubble ${isMe ? 'msg-sent' : 'msg-received'}`;
                    let contentHtml = (!isMe && currentChatId === 'global-room') ? `<span class="msg-sender-name">${msg.senderName || "Unknown"}</span>` : "";
                    contentHtml += msg.videoUrl ? `<div class="shared-vid-card" onclick="openPostViewer('${msg.videoUrl}', false)"><video src="${msg.videoUrl}" preload="metadata"></video></div><p style="margin-top:5px; font-size:0.8rem;">${msg.text}</p>` : msg.text;
                    div.innerHTML = contentHtml; dmMessages.appendChild(div);
                });
                dmMessages.scrollTop = dmMessages.scrollHeight;
            });
        } catch(e) { dmMessages.innerHTML = '<div class="msg-bubble msg-received">Live chat is offline in sandbox mode. 🛑</div>'; }
    }

    document.getElementById('btn-send-dm').addEventListener('click', async () => {
        const input = document.getElementById('dm-input'); const text = input.value.trim();
        if(text !== "" && currentChatId) { input.value = ""; try { await window.firebaseDb.collection('chats').doc(currentChatId).collection('messages').add({ senderId: currentUser.id, senderName: currentUser.name, text: text, timestamp: firebase.firestore.FieldValue.serverTimestamp() }); } catch(e) {} }
    });

    async function shareVideoToLiveChat(url) {
        if(currentChatId) { try { await window.firebaseDb.collection('chats').doc(currentChatId).collection('messages').add({ senderId: currentUser.id, senderName: currentUser.name, text: "Check out this aesthetic video! 🎬", videoUrl: url, timestamp: firebase.firestore.FieldValue.serverTimestamp() }); } catch(e) {} }
    }

    const commentsOverlay = document.getElementById('comments-overlay'); const commentsList = document.getElementById('comments-list');
    function openCommentsModal(postId) {
        currentCommentPostId = postId; commentsOverlay.classList.remove('hidden'); setTimeout(() => commentsOverlay.classList.add('open'), 10);
        commentsList.innerHTML = '<div style="text-align:center; padding: 20px; color:#aaa;">Loading comments... ✨</div>';
        if (commentsUnsubscribe) commentsUnsubscribe();
        try {
            commentsUnsubscribe = window.firebaseDb.collection('posts').doc(postId).collection('comments').orderBy('timestamp', 'asc').onSnapshot(snapshot => {
                commentsList.innerHTML = '';
                if (snapshot.empty) { commentsList.innerHTML = '<div style="text-align:center; padding: 20px; color:#aaa;">Be the first to comment! ✨</div>'; return; }
                snapshot.forEach(doc => {
                    const comment = doc.data(); const item = document.createElement('div'); item.className = 'comment-item';
                    item.innerHTML = `<div class="comment-avatar">🍈</div><div class="comment-content"><h5>${comment.authorName}</h5><p>${comment.text}</p></div>`; commentsList.appendChild(item);
                });
                commentsList.scrollTop = commentsList.scrollHeight; 
            });
        } catch (e) { commentsList.innerHTML = '<div style="text-align:center; padding: 20px; color:#aaa;">Comments unavailable.</div>'; }
    }

    document.getElementById('close-comments').addEventListener('click', () => { commentsOverlay.classList.remove('open'); setTimeout(() => commentsOverlay.classList.add('hidden'), 300); if (commentsUnsubscribe) commentsUnsubscribe(); });
    document.getElementById('btn-send-comment').addEventListener('click', async () => {
        if (!currentUser.uid || currentUser.uid.includes("local")) return alert("Login required! ✨");
        const input = document.getElementById('comment-input'); const text = input.value.trim();
        if (text !== "" && currentCommentPostId) { input.value = ""; try { await window.firebaseDb.collection('posts').doc(currentCommentPostId).collection('comments').add({ authorUid: currentUser.uid, authorName: currentUser.name, text: text, timestamp: firebase.firestore.FieldValue.serverTimestamp() }); } catch(e) {} }
    });

</script>
</body>
</html>
