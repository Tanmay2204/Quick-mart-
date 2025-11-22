# Quick-mart-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Quick Mart</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Load Google Font: Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6; /* gray-100 */
            -webkit-tap-highlight-color: transparent;
        }
        /* Hide scrollbar for clean mobile look */
        .no-scrollbar::-webkit-scrollbar {
            display: none;
        }
        .no-scrollbar {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
        /* Spinner */
        .spinner {
            border: 3px solid rgba(255, 255, 255, 0.3);
            border-left-color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        /* Map Animation */
        .bike-anim { animation: ride 3s linear infinite alternate; }
        @keyframes ride { 0% { transform: translateX(0); } 100% { transform: translateX(30px); } }
        
        /* Voice Pulse */
        .pulse { animation: pulse 1.5s infinite; }
        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.1); opacity: 0.7; }
        }
        
        /* Gradient Text */
        .text-gradient {
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-image: linear-gradient(to right, #16a34a, #059669);
        }
    </style>
</head>
<body class="flex items-center justify-center min-h-screen p-0 sm:p-4 bg-gray-200">

    <!-- Mobile Phone Container -->
    <div class="w-full h-screen sm:h-[850px] sm:max-w-sm bg-gray-50 sm:rounded-[2.5rem] shadow-2xl overflow-hidden flex flex-col relative ring-8 ring-black">

        <!-- 2. App Content (Scrollable) -->
        <div class="flex-grow overflow-y-auto no-scrollbar pb-24" id="main-scroll-area">

            <!-- VIEW: HOME -->
            <div id="app-view" class="p-4 pt-8">
                <!-- Header -->
                <div class="flex justify-between items-start mb-6">
                    <div>
                        <h1 class="text-2xl font-extrabold text-gray-900 tracking-tight">Quick<span class="text-green-600">Mart</span></h1>
                        <div class="flex items-center gap-1 mt-1">
                            <span class="bg-gray-200 text-gray-700 text-[10px] font-bold px-2 py-0.5 rounded uppercase">Home</span>
                            <span class="text-xs text-gray-500 truncate w-32">12 mins to your location</span>
                        </div>
                    </div>
                    <div class="w-10 h-10 bg-white rounded-full flex items-center justify-center shadow-sm border border-gray-100 text-lg">👤</div>
                </div>

                <!-- Search Bar -->
                <div class="bg-white p-1.5 rounded-2xl shadow-sm border border-gray-200 flex items-center gap-2 mb-6 sticky top-2 z-10">
                    <div class="pl-3 text-gray-400">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5">
                            <path stroke-linecap="round" stroke-linejoin="round" d="m21 21-5.197-5.197m0 0A7.5 7.5 0 1 0 5.196 5.196a7.5 7.5 0 0 0 10.607 10.607Z" />
                        </svg>
                    </div>
                    <!-- Smart Placeholder -->
                    <input type="text" id="dish-input" class="flex-grow bg-transparent outline-none text-gray-800 placeholder-gray-400 text-sm py-2" placeholder="Try 'I have eggs & bread'...">
                    <button id="voice-btn" class="p-2.5 rounded-xl bg-gray-100 text-gray-600 hover:bg-green-50 hover:text-green-600 transition-all">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M12 18.75a.375.375 0 0 0 .375-.375v-1.5a.375.375 0 0 0-.75 0v1.5a.375.375 0 0 0 .375.375ZM8.25 15.125a.375.375 0 0 1 .375-.375h.375a.375.375 0 0 1 .375.375v1.5a.375.375 0 0 1-.375.375h-.375a.375.375 0 0 1-.375-.375v-1.5ZM12 12.75a.375.375 0 0 0 .375-.375v-1.5a.375.375 0 0 0-.75 0v1.5a.375.375 0 0 0 .375.375ZM15.75 15.125a.375.375 0 0 1 .375-.375h.375a.375.375 0 0 1 .375.375v1.5a.375.375 0 0 1-.375.375h-.375a.375.375 0 0 1-.375-.375v-1.5Z" />
                            <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 17.25h7.5a.375.375 0 0 0 .375-.375V9.375a.375.375 0 0 0-.375-.375h-7.5a.375.375 0 0 0-.375.375v7.5a.375.375 0 0 0 .375.375Z" />
                            <path stroke-linecap="round" stroke-linejoin="round" d="M12 18.75v.375a.375.375 0 0 1-.375.375h-1.5a.375.375 0 0 1-.375-.375v-.375m3 0v.375a.375.375 0 0 0 .375.375h1.5a.375.375 0 0 0 .375-.375v-.375M12 5.25v-1.5a.375.375 0 0 1 .375-.375h1.5a.375.375 0 0 1 .375.375v1.5m-3 0v-1.5a.375.375 0 0 0-.375-.375h-1.5a.375.375 0 0 0-.375.375v1.5" />
                        </svg>
                    </button>
                </div>

                <!-- Quick Recipes / Popular Dishes -->
                <div class="mb-6">
                    <div class="flex justify-between items-end mb-3 px-1">
                        <h3 class="text-sm font-bold text-gray-800">Popular Dishes</h3>
                        <span class="text-[10px] text-green-600 font-bold bg-green-50 px-2 py-1 rounded-full">Tap to cook</span>
                    </div>
                    <div class="flex gap-3 overflow-x-auto no-scrollbar pb-2" id="quick-recipes-container">
                        <!-- Dynamic Content populated by JS -->
                    </div>
                </div>

                <!-- Action Button -->
                <button id="get-recipe-btn" class="w-full bg-gradient-to-r from-green-600 to-green-500 hover:from-green-700 hover:to-green-600 active:scale-[0.98] text-white font-bold py-4 rounded-2xl shadow-lg shadow-green-200 transition-all flex items-center justify-center gap-2">
                    <span class="text-lg">✨</span>
                    <span id="btn-text">Ask AI Chef</span>
                    <div id="loading-spinner" class="spinner hidden"></div>
                </button>

                <div id="app-error" class="hidden mt-4 p-3 bg-red-50 text-red-600 rounded-xl text-center text-xs font-medium border border-red-100"></div>

                <!-- Results Area -->
                <div id="results-container" class="hidden mt-8">
                    <div class="flex justify-between items-end mb-4 px-1">
                        <h2 id="results-title" class="text-xl font-extrabold text-gray-800 capitalize leading-tight"></h2>
                        <span class="text-[10px] font-medium bg-gray-200 text-gray-600 px-2 py-1 rounded">Est. Market Prices</span>
                    </div>
                    
                    <!-- NEW: Nutrition & Tips Card -->
                    <div class="bg-gradient-to-br from-indigo-50 to-purple-50 p-4 rounded-2xl border border-indigo-100 mb-5 relative overflow-hidden">
                        <div class="absolute top-0 right-0 -mt-2 -mr-2 w-16 h-16 bg-indigo-100 rounded-full opacity-50"></div>
                        <div class="relative z-10">
                            <div class="flex items-center justify-between mb-2">
                                <h3 class="text-sm font-bold text-indigo-900 flex items-center gap-1">
                                    <span>✨</span> AI Chef's Insights
                                </h3>
                                <span id="health-score" class="bg-white text-indigo-600 text-xs font-bold px-2 py-1 rounded shadow-sm">Health Score: --/10</span>
                            </div>
                            <p id="nutrition-text" class="text-xs text-indigo-800 mb-2 font-medium">Analyzing nutrition...</p>
                            <div class="bg-white/60 p-2 rounded-lg">
                                <p class="text-[10px] text-gray-500 uppercase font-bold mb-0.5">💡 Pro Tip</p>
                                <p id="chef-tip" class="text-xs text-gray-700 italic">Loading tip...</p>
                            </div>
                        </div>
                    </div>

                    <!-- Ingredients Grid -->
                    <div id="ingredients-list" class="grid grid-cols-1 gap-3 mb-8">
                        <!-- Dynamic Cards go here -->
                    </div>
                    
                    <!-- Recipe Steps -->
                    <div class="bg-white p-5 rounded-2xl shadow-sm border border-gray-100">
                        <h3 class="text-sm font-bold text-gray-400 uppercase tracking-wider mb-4">Instructions</h3>
                        <ol id="recipe-list" class="list-decimal list-inside space-y-3 text-sm text-gray-700 leading-relaxed font-medium"></ol>
                    </div>
                    
                    <!-- Save List Button -->
                    <button id="save-list-btn" class="hidden mt-6 w-full bg-gray-900 text-white py-3.5 rounded-xl font-bold shadow-md hover:bg-gray-800 transition-all">
                        Save Recipe for Later
                    </button>
                    <div id="save-success" class="hidden mt-2 text-center text-green-600 text-sm font-medium">Successfully saved!</div>
                </div>
            </div>

            <!-- VIEW: SAVED LISTS -->
            <div id="my-lists-view" class="hidden p-4 pt-8">
                <h1 class="text-2xl font-extrabold text-gray-900 mb-6">My Recipes</h1>
                <div id="saved-lists-container" class="space-y-4">
                    <p id="no-lists-msg" class="text-center text-gray-400 mt-20 text-sm">You haven't saved any recipes yet.</p>
                </div>
            </div>
            
            <!-- VIEW: CART -->
            <div id="cart-view" class="hidden p-4 pt-8 flex flex-col min-h-full">
                <h1 class="text-2xl font-extrabold text-gray-900 mb-1">My Cart</h1>
                <p class="text-xs text-gray-500 mb-6 font-medium">Review your items</p>
                
                <div id="cart-items-container" class="space-y-3 flex-grow">
                    <p id="no-cart-msg" class="text-center text-gray-400 mt-20 text-sm">Your cart is empty.</p>
                </div>
                
                <!-- Cart Footer (Floating) -->
                <div id="cart-footer" class="hidden mt-6 bg-white p-5 rounded-2xl shadow-[0_-4px_20px_rgba(0,0,0,0.05)] border border-gray-100">
                    <div class="flex justify-between items-center mb-4">
                        <div class="flex flex-col">
                            <span class="text-xs text-gray-500 font-semibold uppercase">To Pay</span>
                            <span id="cart-total-price" class="text-2xl font-extrabold text-gray-900">₹0</span>
                        </div>
                        <div class="text-right">
                             <span class="text-[10px] text-green-600 font-bold bg-green-50 px-2 py-1 rounded">Free Delivery</span>
                        </div>
                    </div>
                    <button id="place-order-btn" class="w-full bg-green-600 text-white py-3.5 rounded-xl font-bold shadow-lg shadow-green-200 hover:bg-green-700 mb-3 active:scale-[0.99] transition-all">
                        Place Order
                    </button>
                    <button id="clear-cart-btn" class="w-full text-red-500 text-xs font-bold py-2 uppercase tracking-wide">
                        Clear Cart
                    </button>
                </div>
            </div>

            <!-- VIEW: TRACKING (ORDER STATUS) -->
            <div id="tracking-view" class="hidden bg-gray-50 h-full">
                <!-- Map Area -->
                <div class="h-1/2 bg-blue-50 relative overflow-hidden">
                    <!-- Simple CSS Map Pattern -->
                    <div class="absolute inset-0 opacity-10" style="background-image: radial-gradient(#4b5563 1px, transparent 1px); background-size: 20px 20px;"></div>
                    <!-- Path Line -->
                    <div class="absolute top-1/2 left-10 right-10 h-1 bg-gray-300 rounded"></div>
                    <!-- Bike Icon Animation -->
                    <div class="absolute top-1/2 left-1/2 -mt-6 -ml-4 text-4xl bike-anim">🛵</div>
                    <!-- Home Icon -->
                    <div class="absolute top-1/2 right-8 -mt-6 text-3xl">🏠</div>
                    <!-- Store Icon -->
                    <div class="absolute top-1/2 left-8 -mt-6 text-3xl">🏪</div>
                    
                    <div class="absolute bottom-4 left-4 bg-white px-3 py-1 rounded-lg shadow-sm text-xs font-bold text-gray-700">
                        Arriving in <span class="text-green-600">12 mins</span>
                    </div>
                </div>

                <!-- Status Sheet -->
                <div class="h-1/2 bg-white rounded-t-[2rem] -mt-6 relative shadow-[0_-5px_20px_rgba(0,0,0,0.05)] p-6 flex flex-col">
                    <div class="w-12 h-1.5 bg-gray-200 rounded-full mx-auto mb-6"></div>
                    
                    <h2 class="text-xl font-bold text-gray-900 mb-1">Order #4402</h2>
                    <p class="text-sm text-gray-500 mb-6">Preparing your grocery bag</p>

                    <!-- Steps -->
                    <div class="space-y-6 pl-2 border-l-2 border-gray-100 ml-2">
                        <div class="relative pl-6">
                            <div class="absolute -left-[9px] top-0 w-4 h-4 rounded-full bg-green-500 border-4 border-white shadow-sm"></div>
                            <h4 class="text-sm font-bold text-gray-900">Order Placed</h4>
                            <p class="text-xs text-gray-400">10:30 AM</p>
                        </div>
                        <div class="relative pl-6">
                            <div id="step-packed" class="absolute -left-[9px] top-0 w-4 h-4 rounded-full bg-gray-300 border-4 border-white transition-colors duration-500"></div>
                            <h4 class="text-sm font-bold text-gray-900">Packed</h4>
                            <p id="text-packed" class="text-xs text-gray-400">Processing...</p>
                        </div>
                        <div class="relative pl-6">
                            <div id="step-way" class="absolute -left-[9px] top-0 w-4 h-4 rounded-full bg-gray-300 border-4 border-white transition-colors duration-500"></div>
                            <h4 class="text-sm font-bold text-gray-900">On the way</h4>
                            <p class="text-xs text-gray-400">Rider: Ramesh</p>
                        </div>
                    </div>

                    <button id="back-home-btn" class="mt-auto w-full bg-gray-100 text-gray-700 py-3 rounded-xl font-bold hover:bg-gray-200">Back to Home</button>
                </div>
            </div>
            
            <!-- VIEW: PROFILE -->
            <div id="profile-view" class="hidden p-4 pt-8">
                <h1 class="text-2xl font-extrabold text-gray-900 mb-6">Account</h1>
                
                <!-- Guest View -->
                <div id="guest-profile-view" class="hidden space-y-6">
                    <div class="bg-blue-50 p-5 rounded-2xl text-blue-900 text-sm leading-relaxed border border-blue-100">
                        You are currently browsing as a <strong>Guest</strong>. Create an account to save your lists permanently across devices.
                    </div>
                    
                    <div class="space-y-4">
                        <input type="email" id="login-email" placeholder="Email address" class="w-full bg-white px-4 py-3.5 rounded-xl border border-gray-200 focus:border-green-500 outline-none transition-all font-medium">
                        <input type="password" id="login-password" placeholder="Password" class="w-full bg-white px-4 py-3.5 rounded-xl border border-gray-200 focus:border-green-500 outline-none transition-all font-medium">
                    </div>
                    
                    <div class="grid grid-cols-2 gap-3">
                        <button id="login-btn" class="bg-green-600 text-white py-3.5 rounded-xl font-bold hover:bg-green-700 shadow-md transition-all">Login</button>
                        <button id="signup-btn" class="bg-white text-green-600 border-2 border-green-600 py-3.5 rounded-xl font-bold hover:bg-green-50 transition-all">Sign Up</button>
                    </div>
                    <div id="login-error" class="hidden text-red-500 text-xs text-center font-medium bg-red-50 p-2 rounded-lg"></div>
                </div>
                
                <!-- Logged In View -->
                <div id="email-profile-view" class="hidden space-y-6">
                    <div class="bg-white p-5 rounded-2xl border border-gray-100 shadow-sm flex items-center gap-4">
                        <div class="w-14 h-14 bg-gradient-to-br from-green-400 to-green-600 rounded-full flex items-center justify-center text-white font-bold text-xl shadow-md">
                            U
                        </div>
                        <div class="overflow-hidden">
                            <p class="text-xs text-gray-400 font-bold uppercase tracking-wider">Logged in as</p>
                            <p id="user-email" class="text-gray-900 font-bold truncate"></p>
                        </div>
                    </div>
                    
                    <div class="space-y-3">
                        <button id="change-password-btn" class="w-full bg-white text-gray-600 border border-gray-200 py-3.5 rounded-xl font-bold hover:bg-gray-50 text-sm transition-all">Reset Password</button>
                        <button id="logout-btn" class="w-full bg-red-50 text-red-600 py-3.5 rounded-xl font-bold hover:bg-red-100 text-sm transition-all">Log Out</button>
                    </div>
                    <div id="password-reset-success" class="hidden p-3 bg-green-50 text-green-700 rounded-xl text-xs font-medium text-center">Reset link sent to your email!</div>
                </div>
            </div>

        </div> <!-- End App Content -->

        <!-- 3. Bottom Navigation Bar -->
        <div class="absolute bottom-0 w-full bg-white border-t border-gray-100 shadow-[0_-10px_30px_rgba(0,0,0,0.03)] pb-safe pt-1" id="nav-bar">
            <div class="flex justify-around items-end px-2 pb-3">
                <!-- Home -->
                <button id="nav-home" class="flex flex-col items-center p-2 text-green-600 transition-colors w-16">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6 mb-1">
                        <path d="M11.47 3.84a.75.75 0 0 1 1.06 0l8.69 8.69a.75.75 0 1 0 1.06-1.06l-8.689-8.69a2.25 2.25 0 0 0-3.182 0l-8.69 8.69a.75.75 0 0 0 1.061 1.06l8.69-8.69Z" />
                        <path d="m12 5.432 8.159 8.159c.03.03.06.058.091.086v6.198c0 1.035-.84 1.875-1.875 1.875H15a.75.75 0 0 1-.75-.75v-4.5a.75.75 0 0 0-.75-.75h-3a.75.75 0 0 0-.75.75V21a.75.75 0 0 1-.75.75H5.625a1.875 1.875 0 0 1-1.875-1.875v-6.198a2.29 2.29 0 0 0 .091-.
