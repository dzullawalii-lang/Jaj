# Jaj
Jaja
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>🔒 DIZX RANSOMWARE - TIDAK BISA KELUAR</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }
        
        body {
            background: black;
            min-height: 100vh;
            overflow: hidden;
            position: fixed;
            width: 100%;
            height: 100%;
            font-family: 'Courier New', monospace;
        }
        
        .ransom-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, #1a0000, #000000);
            z-index: 9999999999;
            display: flex;
            justify-content: center;
            align-items: center;
            animation: bgPulse 2s infinite;
        }
        
        @keyframes bgPulse {
            0%, 100% { background: radial-gradient(circle, #1a0000, #000000); }
            50% { background: radial-gradient(circle, #3a0000, #000000); }
        }
        
        .ransom-box {
            background: rgba(0,0,0,0.95);
            border: 3px solid #ff0000;
            border-radius: 20px;
            padding: 40px 30px;
            max-width: 500px;
            width: 90%;
            text-align: center;
            box-shadow: 0 0 50px rgba(255,0,0,0.7);
            animation: borderBlink 0.3s infinite;
        }
        
        @keyframes borderBlink {
            0%, 100% { border-color: #ff0000; box-shadow: 0 0 50px rgba(255,0,0,0.5); }
            50% { border-color: #ff4444; box-shadow: 0 0 100px rgba(255,255,0,0.8); }
        }
        
        .lock-icon {
            font-size: 80px;
            animation: shake 0.3s infinite;
            display: inline-block;
        }
        
        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-3px); }
            75% { transform: translateX(3px); }
        }
        
        h1 {
            color: #ff0000;
            font-size: 24px;
            margin: 20px 0;
            text-transform: uppercase;
        }
        
        .message {
            color: #ff6666;
            margin: 15px 0;
            line-height: 1.6;
            font-size: 13px;
        }
        
        .warning {
            color: #ffff00;
            font-size: 14px;
            margin: 15px 0;
            background: rgba(255,0,0,0.2);
            padding: 10px;
            border-radius: 10px;
            font-weight: bold;
        }
        
        .code-input {
            width: 100%;
            padding: 15px;
            font-size: 28px;
            text-align: center;
            background: #111;
            border: 2px solid #ff0000;
            color: #00ff00;
            font-family: monospace;
            letter-spacing: 8px;
            margin: 20px 0;
            border-radius: 10px;
        }
        
        .code-input:focus {
            outline: none;
            border-color: #00ff00;
            background: #1a1a1a;
        }
        
        button {
            background: #ff0000;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 18px;
            font-weight: bold;
            border-radius: 10px;
            cursor: pointer;
            width: 100%;
            margin: 10px 0;
            transition: 0.2s;
        }
        
        button:hover {
            background: #cc0000;
        }
        
        .counter {
            color: #ff6666;
            font-size: 12px;
            margin-top: 15px;
        }
        
        .info {
            color: #888;
            font-size: 11px;
            margin-top: 15px;
        }
    </style>
</head>
<body>
    <div class="ransom-overlay" id="ransomOverlay">
        <div class="ransom-box">
            <div class="lock-icon">🔒💀🔥</div>
            <h1>⚠️ SISTEM ANDA TERKUNCI ⚠️</h1>
            <div class="message">
                <strong>DIZX RANSOMWARE v4.0</strong><br><br>
                <strong>Semua file, foto, dan data pribadi anda</strong><br>
                telah dienkripsi menggunakan algoritma AES-256.<br><br>
                <span style="color: #ffff00;">🔐 SATU-SATUNYA CARA UNTUK KELUAR:</span><br>
                Masukkan <strong style="color: #00ff00;">KODE DEKRIPSI: 123</strong> pada kolom di bawah.
            </div>
            
            <div class="warning">
                💀 JANGAN TUTUP TAB INI! 💀<br>
                <span style="font-size: 11px;">Menutup tab akan menghapus semua data secara permanen</span>
            </div>
            
            <input type="password" class="code-input" id="codeInput" maxlength="3" placeholder="___" autocomplete="off" inputmode="numeric">
            
            <button id="unlockBtn">🔓 DEKRIPSI & KELUAR</button>
            
            <div class="counter" id="attemptCounter">⚠️ HANYA 3 KESEMPATAN ⚠️</div>
            <div class="info">Kode: 123</div>
        </div>
    </div>

    <script>
        (function() {
            const CORRECT_CODE = "123";
            let attemptsLeft = 3;
            let unlocked = false;
            
            const overlay = document.getElementById('ransomOverlay');
            const codeInput = document.getElementById('codeInput');
            const unlockBtn = document.getElementById('unlockBtn');
            const attemptCounter = document.getElementById('attemptCounter');
            
            // ========== TEKNIK SUPER LOCK - GAK BISA KELUAR SAMA SEKALI ==========
            
            // 1. Fullscreen paksa terus-menerus
            function forceFullscreen() {
                const docEl = document.documentElement;
                const methods = [
                    () => docEl.requestFullscreen(),
                    () => docEl.webkitRequestFullscreen(),
                    () => docEl.msRequestFullscreen()
                ];
                
                for (let method of methods) {
                    try { method(); } catch(e) {}
                }
            }
            
            // Paksa fullscreen setiap 500ms
            setInterval(forceFullscreen, 500);
            
            // 2. Block SEMUA keyboard yang bisa dipake keluar
            document.addEventListener('keydown', function(e) {
                // Block semua tombol function dan shortcut
                const blocked = [
                    'Escape', 'F1', 'F2', 'F3', 'F4', 'F5', 'F6', 'F7', 'F8', 'F9', 'F10', 'F11', 'F12',
                    'Alt', 'Control', 'Meta', 'Windows', 'Tab', 'Home', 'End', 'PageUp', 'PageDown',
                    'Delete', 'Insert', 'ContextMenu', 'Backspace', 'ArrowLeft', 'ArrowRight'
                ];
                
                // Block Ctrl+ apapun
                if (e.ctrlKey || e.altKey || e.metaKey) {
                    e.preventDefault();
                    e.stopPropagation();
                    return false;
                }
                
                // Block tombol tertentu
                if (blocked.includes(e.key)) {
                    e.preventDefault();
                    e.stopPropagation();
                    return false;
                }
                
                // Block F5, Ctrl+R, Ctrl+Shift+R
                if (e.key === 'F5' || 
                    (e.ctrlKey && (e.key === 'r' || e.key === 'R')) ||
                    (e.ctrlKey && e.shiftKey && (e.key === 'r' || e.key === 'R'))) {
                    e.preventDefault();
                    return false;
                }
                
                // Block Alt+F4
                if (e.altKey && e.key === 'F4') {
                    e.preventDefault();
                    return false;
                }
            });
            
            // 3. Block right click dan inspect element
            document.addEventListener('contextmenu', function(e) {
                e.preventDefault();
                return false;
            });
            
            // 4. Block F12 dan devtools shortcuts
            window.addEventListener('keydown', function(e) {
                if (e.key === 'F12') {
                    e.preventDefault();
                    return false;
                }
                if (e.ctrlKey && e.shiftKey && (e.key === 'I' || e.key === 'J' || e.key === 'C')) {
                    e.preventDefault();
                    return false;
                }
                if (e.ctrlKey && e.key === 'u') {
                    e.preventDefault();
                    return false;
                }
            });
            
            // 5. Block history back/forward (gak bisa pake tombol back browser)
            history.pushState(null, null, location.href);
            window.addEventListener('popstate', function() {
                if (!unlocked) {
                    history.pushState(null, null, location.href);
                }
            });
            setInterval(() => {
                if (!unlocked) {
                    history.pushState(null, null, location.href);
                }
            }, 100);
            
            // 6. Block close tab (beforeunload)
            window.addEventListener('beforeunload', function(e) {
                if (!unlocked) {
                    e.preventDefault();
                    e.returnValue = '⚠️ PERINGATAN! ⚠️\n\nMenutup tab akan menghapus semua data anda secara permanen!\nMasukkan kode dekripsi 123 untuk keluar dengan selamat.';
                    return '⚠️ PERINGATAN! ⚠️\n\nMenutup tab akan menghapus semua data anda secara permanen!\nMasukkan kode dekripsi 123 untuk keluar dengan selamat.';
                }
            });
            
            // 7. Block touch gesture (swipe back) di mobile
            let touchStart = 0;
            document.addEventListener('touchstart', function(e) {
                touchStart = e.touches[0].clientX;
            });
            document.addEventListener('touchmove', function(e) {
                const touchEnd = e.touches[0].clientX;
                if (touchEnd - touchStart > 50) {
                    e.preventDefault();
                }
            });
            
            // 8. Block copy, cut, paste
            document.addEventListener('copy', (e) => e.preventDefault());
            document.addEventListener('cut', (e) => e.preventDefault());
            document.addEventListener('paste', (e) => e.preventDefault());
            
            // 9. Block drag and drop
            document.addEventListener('dragstart', (e) => e.preventDefault());
            
            // 10. Block select all text
            document.addEventListener('selectstart', (e) => e.preventDefault());
            
            // ========== UNLOCK FUNCTION - KALO KODE BENER, KELUAR DARI WEB ==========
            function unlockAndExit() {
                const inputCode = codeInput.value;
                
                if (inputCode === CORRECT_CODE) {
                    unlocked = true;
                    
                    // Hapus block beforeunload biar bisa keluar
                    window.removeEventListener('beforeunload', () => {});
                    
                    // Exit fullscreen dulu
                    if (document.exitFullscreen) {
                        document.exitFullscreen();
                    }
                    if (document.webkitExitFullscreen) {
                        document.webkitExitFullscreen();
                    }
                    
                    // Tampilkan pesan sukses sebentar
                    document.body.innerHTML = `
                        <div style="background: black; color: #00ff00; text-align: center; padding: 100px; height: 100vh; font-family: monospace;">
                            <h1 style="color: #00ff00; font-size: 48px;">✅ DEKRIPSI BERHASIL ✅</h1>
                            <p style="color: #00ff00; font-size: 20px; margin-top: 30px;">Semua file telah didekripsi!</p>
                            <p style="color: #00ff00; font-size: 18px; margin-top: 20px;">Anda akan keluar secara otomatis...</p>
                            <div style="margin-top: 50px;">👑 DIZX RANSOMWARE 👑</div>
                        </div>
                    `;
                    
                    // Setelah 2 detik, tutup tab/window
                    setTimeout(() => {
                        window.close();
                        
                        // Fallback: redirect ke about:blank (biar keluar dari web ini)
                        window.location.href = "about:blank";
                        
                        // Alternative: redirect ke Google
                        setTimeout(() => {
                            window.location.href = "https://www.google.com";
                        }, 100);
                    }, 2000);
                    
                } else {
                    // KODE SALAH
                    attemptsLeft--;
                    
                    if (attemptsLeft > 0) {
                        attemptCounter.innerHTML = `❌ KODE SALAH! ❌<br>Kesempatan tersisa: ${attemptsLeft}`;
                        codeInput.value = '';
                        codeInput.style.borderColor = '#ff0000';
                        
                        // Efek goyang
                        const box = document.querySelector('.ransom-box');
                        box.style.animation = 'none';
                        setTimeout(() => {
                            box.style.animation = 'shake 0.3s ease-in-out';
                        }, 10);
                        setTimeout(() => {
                            box.style.animation = '';
                            codeInput.style.borderColor = '#ff0000';
                        }, 300);
                    } else {
                        // KESEMPATAN HABIS - GUNAKAN TEKANAN PSIKOLOGIS
                        attemptCounter.innerHTML = `💀 KESEMPATAN HABIS! 💀<br>Data akan dihapus dalam 10 detik...`;
                        codeInput.disabled = true;
                        unlockBtn.disabled = true;
                        codeInput.style.opacity = '0.5';
                        unlockBtn.style.opacity = '0.5';
                        
                        let countdown = 10;
                        const countdownInterval = setInterval(() => {
                            countdown--;
                            attemptCounter.innerHTML = `💀 KESEMPATAN HABIS! 💀<br>Data akan dihapus dalam ${countdown} detik...`;
                            
                            if (countdown <= 0) {
                                clearInterval(countdownInterval);
                                // Simulasi "penghapusan data" dan redirect
                                document.body.innerHTML = `
                                    <div style="background: black; color: red; text-align: center; padding: 100px; height: 100vh; font-family: monospace;">
                                        <h1 style="color: red; font-size: 48px;">💀 DATA HAPUS PERMANEN 💀</h1>
                                        <p style="color: red; font-size: 20px; margin-top: 30px;">Semua file anda telah dihapus!</p>
                                        <p style="color: #888; font-size: 14px; margin-top: 50px;">DIZX RANSOMWARE - www.dizx.com</p>
                                    </div>
                                `;
                                setTimeout(() => {
                                    window.location.href = "about:blank";
                                }, 3000);
                            }
                        }, 1000);
                    }
                }
            }
            
            // Event listener
            unlockBtn.addEventListener('click', unlockAndExit);
            codeInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    unlockAndExit();
                }
            });
            
            // Auto focus
            setTimeout(() => {
                codeInput.focus();
            }, 100);
            
            // Force focus terus biar gak bisa pindah
            setInterval(() => {
                if (document.activeElement !== codeInput && !unlocked) {
                    codeInput.focus();
                }
            }, 100);
            
            // Block alert buat ngurangin kemungkinan user pake console
            window.alert = function() {};
            window.confirm = function() { return false; };
            window.prompt = function() { return null; };
            
            // Matikan console.log yang berguna buat debugging
            console.log = function() {};
            console.warn = function() {};
            console.error = function() {};
            
            console.log("%c🔒 DIZX RANSOMWARE - MASUKKAN 123 UNTUK KELUAR 🔒", "color: red; font-size: 20px");
        })();
    </script>
</body>
</html>
