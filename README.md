<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FinTrack - Boutique & Order Management Dashboard</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        finRed: '#7f1d1d',   /* Dark Red */
                        finGreen: '#064e3b', /* Dark Green */
                        finBlue: '#1e3a8a',  /* Dark Blue */
                        darkBg: '#0f172a',
                        cardBg: '#1e293b'
                    }
                }
            }
        }
    </script>
</head>
<body class="bg-darkBg text-slate-100 font-sans min-h-screen flex flex-col">

    <!-- Top Navbar -->
    <header class="bg-slate-900 border-b border-slate-800 sticky top-0 z-50 shadow-md">
        <div class="max-w-7xl mx-auto px-4 py-3 flex justify-between items-center">
            <div class="flex items-center space-x-3">
                <div class="bg-gradient-to-r from-finRed via-finBlue to-finGreen p-2 rounded-xl text-white shadow-lg">
                    <i class="fa-solid fa-chart-pie text-xl"></i>
                </div>
                <div>
                    <h1 class="text-xl font-bold tracking-wide bg-gradient-to-r from-red-400 via-blue-400 to-emerald-400 bg-clip-text text-transparent">Boutique Finance Pro</h1>
                    <p class="text-xs text-slate-400">Financial & Order Analytics Hub</p>
                </div>
            </div>
            <div class="flex items-center space-x-3">
                <button onclick="openNewOrderModal()" class="bg-emerald-700 hover:bg-emerald-800 text-white px-4 py-2 rounded-lg text-sm font-semibold shadow transition flex items-center space-x-2">
                    <i class="fa-solid fa-plus"></i><span>New Order / Customer</span>
                </button>
            </div>
        </div>
    </header>

    <!-- Main Container -->
    <div class="max-w-7xl mx-auto px-4 py-6 flex-1 w-full grid grid-cols-1 md:grid-cols-5 gap-6">
        
        <!-- Sidebar Navigation -->
        <aside class="md:col-span-1 bg-cardBg border border-slate-800 rounded-2xl p-4 flex flex-col justify-between shadow-xl">
            <nav class="space-y-2">
                <button onclick="switchTab('dashboard')" id="nav-dashboard" class="w-full flex items-center space-x-3 px-4 py-3 rounded-xl text-sm font-medium transition bg-finBlue text-white shadow">
                    <i class="fa-solid fa-gauge w-5"></i><span>Dashboard</span>
                </button>
                <button onclick="switchTab('customers')" id="nav-customers" class="w-full flex items-center space-x-3 px-4 py-3 rounded-xl text-sm font-medium transition text-slate-300 hover:bg-slate-800 hover:text-white">
                    <i class="fa-solid fa-users w-5"></i><span>Customers & Orders</span>
                </button>
                <button onclick="switchTab('employees')" id="nav-employees" class="w-full flex items-center space-x-3 px-4 py-3 rounded-xl text-sm font-medium transition text-slate-300 hover:bg-slate-800 hover:text-white">
                    <i class="fa-solid fa-user-tie w-5"></i><span>Employees</span>
                </button>
                <button onclick="switchTab('store')" id="nav-store" class="w-full flex items-center space-x-3 px-4 py-3 rounded-xl text-sm font-medium transition text-slate-300 hover:bg-slate-800 hover:text-white">
                    <i class="fa-solid fa-store w-5"></i><span>Item Store</span>
                </button>
                <button onclick="switchTab('reports')" id="nav-reports" class="w-full flex items-center space-x-3 px-4 py-3 rounded-xl text-sm font-medium transition text-slate-300 hover:bg-slate-800 hover:text-white">
                    <i class="fa-solid fa-file-invoice-dollar w-5"></i><span>Reports & Data</span>
                </button>
            </nav>
            <div class="pt-4 border-t border-slate-800 text-xs text-slate-500 text-center">
                Financial Theme v1.0 <br>GitHub Hosted Ready
            </div>
        </aside>

        <!-- Main Content Area -->
        <main class="md:col-span-4 space-y-6">

            <!-- 1. DASHBOARD TAB -->
            <section id="tab-dashboard" class="space-y-6">
                <!-- Top Summary Financial Cards -->
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                    <div class="bg-cardBg border border-finBlue/40 p-5 rounded-2xl shadow-lg relative overflow-hidden">
                        <div class="absolute right-3 top-3 text-blue-500/20 text-4xl"><i class="fa-solid fa-wallet"></i></div>
                        <p class="text-xs uppercase tracking-wider text-slate-400 font-semibold">Total Revenue</p>
                        <h3 class="text-2xl font-bold mt-2 text-blue-400" id="dash-total-revenue">₹0</h3>
                        <span class="text-xs text-emerald-400 mt-1 inline-block"><i class="fa-solid fa-arrow-trend-up"></i> Overall Earnings</span>
                    </div>
                    <div class="bg-cardBg border border-finGreen/40 p-5 rounded-2xl shadow-lg relative overflow-hidden">
                        <div class="absolute right-3 top-3 text-emerald-500/20 text-4xl"><i class="fa-solid fa-sack-dollar"></i></div>
                        <p class="text-xs uppercase tracking-wider text-slate-400 font-semibold">Total Profit</p>
                        <h3 class="text-2xl font-bold mt-2 text-emerald-400" id="dash-total-profit">₹0</h3>
                        <span class="text-xs text-emerald-400 mt-1 inline-block"><i class="fa-solid fa-circle-check"></i> Net Gain</span>
                    </div>
                    <div class="bg-cardBg border border-pink-900/40 p-5 rounded-2xl shadow-lg relative overflow-hidden">
                        <div class="absolute right-3 top-3 text-pink-500/20 text-4xl"><i class="fa-solid fa-child"></i></div>
                        <p class="text-xs uppercase tracking-wider text-slate-400 font-semibold">Baby Platform</p>
                        <div class="mt-2 flex justify-between items-end">
                            <div>
                                <span class="text-xs text-slate-400">Rev:</span> <span class="font-bold text-pink-400" id="dash-baby-rev">₹0</span>
                            </div>
                            <div>
                                <span class="text-xs text-slate-400">Prof:</span> <span class="font-bold text-emerald-400" id="dash-baby-prof">₹0</span>
                            </div>
                        </div>
                    </div>
                    <div class="bg-cardBg border border-finRed/40 p-5 rounded-2xl shadow-lg relative overflow-hidden">
                        <div class="absolute right-3 top-3 text-red-500/20 text-4xl"><i class="fa-solid fa-person-dress"></i></div>
                        <p class="text-xs uppercase tracking-wider text-slate-400 font-semibold">Lady Platform</p>
                        <div class="mt-2 flex justify-between items-end">
                            <div>
                                <span class="text-xs text-slate-400">Rev:</span> <span class="font-bold text-red-400" id="dash-lady-rev">₹0</span>
                            </div>
                            <div>
                                <span class="text-xs text-slate-400">Prof:</span> <span class="font-bold text-emerald-400" id="dash-lady-prof">₹0</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Order Status Metrics Row -->
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div class="bg-cardBg border border-slate-800 p-5 rounded-2xl flex items-center justify-between">
                        <div>
                            <p class="text-sm text-slate-400">Completed Orders</p>
                            <h3 class="text-3xl font-bold text-emerald-400 mt-1" id="dash-completed-count">0</h3>
                        </div>
                        <div class="bg-emerald-950 p-4 rounded-xl text-emerald-400 text-2xl">
                            <i class="fa-solid fa-clipboard-check"></i>
                        </div>
                    </div>
                    <div class="bg-cardBg border border-slate-800 p-5 rounded-2xl flex items-center justify-between">
                        <div>
                            <p class="text-sm text-slate-400">Pending Orders (To Complete)</p>
                            <h3 class="text-3xl font-bold text-amber-400 mt-1" id="dash-pending-count">0</h3>
                        </div>
                        <div class="bg-amber-950 p-4 rounded-xl text-amber-400 text-2xl">
                            <i class="fa-solid fa-clock-rotate-left"></i>
                        </div>
                    </div>
                </div>

                <!-- Action Buttons and Pending List -->
                <div class="bg-cardBg border border-slate-800 rounded-2xl p-6 shadow-xl space-y-4">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4">
                        <h2 class="text-lg font-bold flex items-center space-x-2">
                            <i class="fa-solid fa-list-check text-blue-400"></i><span>Active Customer Orders Queue</span>
                        </h2>
                        <div class="flex space-x-2">
                            <button onclick="openNewOrderModal()" class="bg-finBlue hover:bg-blue-800 text-white px-3 py-1.5 rounded-lg text-xs font-semibold shadow">
                                <i class="fa-solid fa-user-plus mr-1"></i> Add New Customer
                            </button>
                            <button onclick="openNewEmployeeModal()" class="bg-finRed hover:bg-red-900 text-white px-3 py-1.5 rounded-lg text-xs font-semibold shadow">
                                <i class="fa-solid fa-user-tie mr-1"></i> Add New Employee
                            </button>
                        </div>
                    </div>

                    <div class="overflow-x-auto">
                        <table class="w-full text-left text-sm text-slate-300">
                            <thead class="bg-slate-900 text-slate-400 uppercase text-xs">
                                <tr>
                                    <th class="p-3">Customer Name</th>
                                    <th class="p-3">Platform & Dress</th>
                                    <th class="p-3">Delivery Date</th>
                                    <th class="p-3">Stitcher</th>
                                    <th class="p-3">Status / Action</th>
                                </tr>
                            </thead>
                            <tbody id="active-orders-table" class="divide-y divide-slate-800">
                                <!-- Dynamic Rows -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- 2. CUSTOMERS & ORDERS TAB -->
            <section id="tab-customers" class="space-y-6 hidden">
                <div class="bg-cardBg border border-slate-800 rounded-2xl p-6 shadow-xl space-y-4">
                    <div class="flex justify-between items-center">
                        <h2 class="text-lg font-bold flex items-center space-x-2">
                            <i class="fa-solid fa-users text-emerald-400"></i><span>All Customers & History</span>
                        </h2>
                        <span class="text-xs text-slate-400">Click customer row to view full profile details</span>
                    </div>

                    <div class="overflow-x-auto">
                        <table class="w-full text-left text-sm text-slate-300">
                            <thead class="bg-slate-900 text-slate-400 uppercase text-xs">
                                <tr>
                                    <th class="p-3">Name</th>
                                    <th class="p-3">WhatsApp</th>
                                    <th class="p-3">Total Orders</th>
                                    <th class="p-3">Total Paid Amount</th>
                                    <th class="p-3">Total Profit Generated</th>
                                    <th class="p-3">Action</th>
                                </tr>
                            </thead>
                            <tbody id="customers-table" class="divide-y divide-slate-800">
                                <!-- Dynamic Customers -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Completed Orders Archive -->
                <div class="bg-cardBg border border-slate-800 rounded-2xl p-6 shadow-xl space-y-4">
                    <h2 class="text-lg font-bold flex items-center space-x-2 text-emerald-400">
                        <i class="fa-solid fa-box-archive"></i><span>Completed Orders Archive</span>
                    </h2>
                    <div class="overflow-x-auto">
                        <table class="w-full text-left text-sm text-slate-300">
                            <thead class="bg-slate-900 text-slate-400 uppercase text-xs">
                                <tr>
                                    <th class="p-3">Customer</th>
                                    <th class="p-3">Dress & Platform</th>
                                    <th class="p-3">Price</th>
                                    <th class="p-3">Profit</th>
                                    <th class="p-3">Completed Date</th>
                                </tr>
                            </thead>
                            <tbody id="completed-orders-table" class="divide-y divide-slate-800">
                                <!-- Dynamic Completed -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- 3. EMPLOYEES TAB -->
            <section id="tab-employees" class="space-y-6 hidden">
                <div class="bg-cardBg border border-slate-800 rounded-2xl p-6 shadow-xl space-y-4">
                    <div class="flex justify-between items-center">
                        <h2 class="text-lg font-bold flex items-center space-x-2">
                            <i class="fa-solid fa-user-tie text-red-400"></i><span>Stitching Staff / Employees</span>
                        </h2>
                        <button onclick="openNewEmployeeModal()" class="bg-finRed hover:bg-red-900 text-white px-3 py-1.5 rounded-lg text-xs font-semibold shadow">
                            <i class="fa-solid fa-plus mr-1"></i> Add Employee
                        </button>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4" id="employees-grid">
                        <!-- Dynamic Employee Cards -->
                    </div>
                </div>
            </section>

            <!-- 4. ITEM STORE TAB -->
            <section id="tab-store" class="space-y-6 hidden">
                <div class="bg-cardBg border border-slate-800 rounded-2xl p-6 shadow-xl space-y-4">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4">
                        <h2 class="text-lg font-bold flex items-center space-x-2">
                            <i class="fa-solid fa-store text-blue-400"></i><span>Item Store & Catalog (Max 5MB Image)</span>
                        </h2>
                        <button onclick="openNewItemModal()" class="bg-finBlue hover:bg-blue-800 text-white px-3 py-1.5 rounded-lg text-xs font-semibold shadow">
                            <i class="fa-solid fa-camera mr-1"></i> Upload New Item
                        </button>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4" id="item-store-grid">
                        <!-- Dynamic Store Items -->
                    </div>
                </div>
            </section>

            <!-- 5. REPORTS TAB -->
            <section id="tab-reports" class="space-y-6 hidden">
                <div class="bg-cardBg border border-slate-800 rounded-2xl p-6 shadow-xl space-y-4">
                    <h2 class="text-lg font-bold flex items-center space-x-2 text-emerald-400">
                        <i class="fa-solid fa-chart-line"></i><span>Advanced Data Analysis & Reports</span>
                    </h2>
                    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                        <div class="bg-slate-900 p-4 rounded-xl border border-slate-800">
                            <p class="text-xs text-slate-400">Filter By Month / Period</p>
                            <select id="report-month-filter" onchange="renderReports()" class="w-full bg-slate-800 border border-slate-700 rounded-lg p-2 mt-2 text-sm text-slate-200">
                                <option value="all">All Time History</option>
                                <option value="current">Current Month</option>
                            </select>
                        </div>
                        <div class="bg-slate-900 p-4 rounded-xl border border-slate-800">
                            <p class="text-xs text-slate-400">Total Analyzed Revenue</p>
                            <h3 class="text-xl font-bold text-blue-400 mt-1" id="rep-revenue">₹0</h3>
                        </div>
                        <div class="bg-slate-900 p-4 rounded-xl border border-slate-800">
                            <p class="text-xs text-slate-400">Total Analyzed Profit</p>
                            <h3 class="text-xl font-bold text-emerald-400 mt-1" id="rep-profit">₹0</h3>
                        </div>
                    </div>

                    <div class="pt-4 border-t border-slate-800">
                        <h3 class="text-sm font-semibold text-slate-300 mb-3">Performance Breakdown Summary</h3>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 text-sm">
                            <div class="bg-slate-900/60 p-4 rounded-xl border border-slate-800 flex justify-between">
                                <span class="text-slate-400">Total Work Orders Received:</span>
                                <span class="font-bold text-white" id="rep-total-orders">0</span>
                            </div>
                            <div class="bg-slate-900/60 p-4 rounded-xl border border-slate-800 flex justify-between">
                                <span class="text-slate-400">Completed Works Rate:</span>
                                <span class="font-bold text-emerald-400" id="rep-completion-rate">0%</span>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

        </main>
    </div>

    <!-- MODAL: NEW ORDER / CUSTOMER -->
    <div id="modal-new-order" class="fixed inset-0 bg-black/70 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-cardBg border border-slate-700 rounded-2xl w-full max-w-lg p-6 shadow-2xl space-y-4 max-h-[90vh] overflow-y-auto">
            <div class="flex justify-between items-center border-b border-slate-800 pb-3">
                <h3 class="text-lg font-bold text-white"><i class="fa-solid fa-file-circle-plus text-emerald-400 mr-2"></i>Add New Customer & Order</h3>
                <button onclick="closeModal('modal-new-order')" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            
            <form id="form-new-order" onsubmit="handleSaveOrder(event)" class="space-y-4 text-sm">
                <div>
                    <label class="block text-slate-400 mb-1">Customer Name</label>
                    <input type="text" id="ord-customer" required class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100 focus:outline-none focus:border-blue-500">
                </div>
                <div>
                    <label class="block text-slate-400 mb-1">WhatsApp Number</label>
                    <input type="tel" id="ord-whatsapp" required class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100 focus:outline-none focus:border-blue-500">
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div>
                        <label class="block text-slate-400 mb-1">Platform Category</label>
                        <select id="ord-platform" class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100 focus:outline-none">
                            <option value="Baby">Baby Platform</option>
                            <option value="Lady">Lady Platform</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-slate-400 mb-1">Dress Name / Item</label>
                        <input type="text" id="ord-dress" required class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100">
                    </div>
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div>
                        <label class="block text-slate-400 mb-1">Delivery Date</label>
                        <input type="date" id="ord-date" required class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100">
                    </div>
                    <div>
                        <label class="block text-slate-400 mb-1">Total Price (₹)</label>
                        <input type="number" id="ord-price" oninput="calculateAdvanceAndProfit()" required class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100">
                    </div>
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div>
                        <label class="block text-slate-400 mb-1">Advance (50% Auto)</label>
                        <input type="number" id="ord-advance" readonly class="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 text-emerald-400 font-bold">
                    </div>
                    <div>
                        <label class="block text-slate-400 mb-1">Total Expense (₹)</label>
                        <input type="number" id="ord-expense" oninput="calculateAdvanceAndProfit()" required class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100">
                        <p id="advance-hint" class="text-xs text-amber-400 mt-1">Remaining Advance after Expense: ₹0</p>
                    </div>
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div>
                        <label class="block text-slate-400 mb-1">Stitching Employee</label>
                        <select id="ord-employee" class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100">
                            <!-- Populated dynamic -->
                        </select>
                    </div>
                    <div>
                        <label class="block text-slate-400 mb-1">Stitching Charge (₹)</label>
                        <input type="number" id="ord-stitch-charge" oninput="calculateAdvanceAndProfit()" required class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100">
                    </div>
                </div>
                <div class="bg-slate-900 p-3 rounded-lg border border-slate-800 flex justify-between items-center">
                    <span class="text-slate-400 font-semibold">Calculated Net Profit:</span>
                    <span class="text-lg font-bold text-emerald-400" id="ord-calculated-profit">₹0</span>
                </div>
                <div class="flex justify-end space-x-3 pt-3">
                    <button type="button" onclick="closeModal('modal-new-order')" class="bg-slate-800 px-4 py-2 rounded-lg text-slate-300">Cancel</button>
                    <button type="submit" class="bg-emerald-700 hover:bg-emerald-800 text-white px-5 py-2 rounded-lg font-semibold shadow">Save Order</button>
                </div>
            </form>
        </div>
    </div>

    <!-- MODAL: NEW EMPLOYEE -->
    <div id="modal-new-employee" class="fixed inset-0 bg-black/70 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-cardBg border border-slate-700 rounded-2xl w-full max-w-sm p-6 shadow-2xl space-y-4">
            <div class="flex justify-between items-center border-b border-slate-800 pb-3">
                <h3 class="text-lg font-bold text-white">Add Stitching Employee</h3>
                <button onclick="closeModal('modal-new-employee')" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form onsubmit="handleSaveEmployee(event)" class="space-y-4 text-sm">
                <div>
                    <label class="block text-slate-400 mb-1">Employee Name</label>
                    <input type="text" id="emp-name" required class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100">
                </div>
                <div>
                    <label class="block text-slate-400 mb-1">Specialization / Role</label>
                    <input type="text" id="emp-role" placeholder="e.g. Master Tailor / Senior Stitcher" required class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100">
                </div>
                <div class="flex justify-end space-x-3 pt-3">
                    <button type="button" onclick="closeModal('modal-new-employee')" class="bg-slate-800 px-4 py-2 rounded-lg text-slate-300">Cancel</button>
                    <button type="submit" class="bg-finRed hover:bg-red-900 text-white px-4 py-2 rounded-lg font-semibold shadow">Save Employee</button>
                </div>
            </form>
        </div>
    </div>

    <!-- MODAL: NEW ITEM STORE UPLOAD -->
    <div id="modal-new-item" class="fixed inset-0 bg-black/70 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-cardBg border border-slate-700 rounded-2xl w-full max-w-sm p-6 shadow-2xl space-y-4">
            <div class="flex justify-between items-center border-b border-slate-800 pb-3">
                <h3 class="text-lg font-bold text-white">Upload Store Item (Max 5MB)</h3>
                <button onclick="closeModal('modal-new-item')" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form onsubmit="handleSaveItem(event)" class="space-y-4 text-sm">
                <div>
                    <label class="block text-slate-400 mb-1">Item Title</label>
                    <input type="text" id="item-title" required class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2.5 text-slate-100">
                </div>
                <div>
                    <label class="block text-slate-400 mb-1">Select Image (Max 5MB)</label>
                    <input type="file" id="item-image" accept="image/*" required onchange="validateImageSize(this)" class="w-full text-xs text-slate-400 file:mr-4 file:py-2 file:px-4 file:rounded-lg file:border-0 file:text-xs file:font-semibold file:bg-blue-900 file:text-blue-200 hover:file:bg-blue-800">
                </div>
                <div class="flex justify-end space-x-3 pt-3">
                    <button type="button" onclick="closeModal('modal-new-item')" class="bg-slate-800 px-4 py-2 rounded-lg text-slate-300">Cancel</button>
                    <button type="submit" class="bg-finBlue hover:bg-blue-800 text-white px-4 py-2 rounded-lg font-semibold shadow">Upload Item</button>
                </div>
            </form>
        </div>
    </div>

    <!-- MODAL: CUSTOMER PROFILE DETAILS -->
    <div id="modal-customer-profile" class="fixed inset-0 bg-black/70 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-cardBg border border-slate-700 rounded-2xl w-full max-w-xl p-6 shadow-2xl space-y-4 max-h-[90vh] overflow-y-auto">
            <div class="flex justify-between items-center border-b border-slate-800 pb-3">
                <h3 class="text-lg font-bold text-white flex items-center space-x-2"><i class="fa-solid fa-user-gear text-blue-400"></i><span id="profile-cust-name">Customer Profile</span></h3>
                <button onclick="closeModal('modal-customer-profile')" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <div class="grid grid-cols-3 gap-4 text-center">
                <div class="bg-slate-900 p-3 rounded-xl border border-slate-800">
                    <span class="text-xs text-slate-400">Total Orders</span>
                    <h4 class="text-lg font-bold text-white mt-1" id="profile-total-orders">0</h4>
                </div>
                <div class="bg-slate-900 p-3 rounded-xl border border-slate-800">
                    <span class="text-xs text-slate-400">Total Cash Paid</span>
                    <h4 class="text-lg font-bold text-blue-400 mt-1" id="profile-total-cash">₹0</h4>
                </div>
                <div class="bg-slate-900 p-3 rounded-xl border border-slate-800">
                    <span class="text-xs text-slate-400">Total Profit Generated</span>
                    <h4 class="text-lg font-bold text-emerald-400 mt-1" id="profile-total-profit">₹0</h4>
                </div>
            </div>
            <div>
                <h4 class="text-sm font-semibold text-slate-300 mb-2">Order History Details</h4>
                <div class="overflow-x-auto">
                    <table class="w-full text-left text-xs text-slate-300">
                        <thead class="bg-slate-900 text-slate-400 uppercase">
                            <tr>
                                <th class="p-2.5">Dress / Platform</th>
                                <th class="p-2.5">Date</th>
                                <th class="p-2.5">Price</th>
                                <th class="p-2.5">Profit</th>
                                <th class="p-2.5">Status</th>
                            </tr>
                        </thead>
                        <tbody id="profile-orders-list" class="divide-y divide-slate-800">
                            <!-- Populated dynamic -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>

    <!-- JavaScript Application Logic -->
    <script>
        // LocalStorage App State
        let state = {
            orders: JSON.parse(localStorage.getItem('b_orders')) || [
                { id: 1, customer: 'Anusree', whatsapp: '9847012345', platform: 'Baby', dress: 'Baby Frock', date: '2026-06-10', price: 2000, advance: 1000, expense: 400, employee: 'Rameshan', stitchCharge: 500, profit: 1100, status: 'Pending' },
                { id: 2, customer: 'Fathima', whatsapp: '9567812345', platform: 'Lady', dress: 'Designer Salwar', date: '2026-06-12', price: 3500, advance: 1750, expense: 800, employee: 'Sruthi', stitchCharge: 900, profit: 1800, status: 'Completed', completedDate: '2026-06-08' }
            ],
            employees: JSON.parse(localStorage.getItem('b_employees')) || [
                { id: 1, name: 'Rameshan', role: 'Master Tailor' },
                { id: 2, name: 'Sruthi', role: 'Designer Specialist' }
            ],
            items: JSON.parse(localStorage.getItem('b_items')) || []
        };

        function saveData() {
            localStorage.setItem('b_orders', JSON.stringify(state.orders));
            localStorage.setItem('b_employees', JSON.stringify(state.employees));
            localStorage.setItem('b_items', JSON.stringify(state.items));
            refreshUI();
        }

        // Tab Switching Logic
        function switchTab(tabId) {
            ['dashboard', 'customers', 'employees', 'store', 'reports'].forEach(t => {
                document.getElementById(`tab-${t}`).classList.add('hidden');
                document.getElementById(`nav-${t}`).className = "w-full flex items-center space-x-3 px-4 py-3 rounded-xl text-sm font-medium transition text-slate-300 hover:bg-slate-800 hover:text-white";
            });
            document.getElementById(`tab-${tabId}`).classList.remove('hidden');
            document.getElementById(`nav-${tabId}`).className = "w-full flex items-center space-x-3 px-4 py-3 rounded-xl text-sm font-medium transition bg-finBlue text-white shadow";
            if(tabId === 'reports') renderReports();
        }

        // Modals Control
        function openNewOrderModal() {
            populateEmployeeDropdown();
            document.getElementById('form-new-order').reset();
            document.getElementById('ord-advance').value = '';
            document.getElementById('advance-hint').innerText = 'Remaining Advance after Expense: ₹0';
            document.getElementById('ord-calculated-profit').innerText = '₹0';
            document.getElementById('modal-new-order').classList.remove('hidden');
        }
        function openNewEmployeeModal() {
            document.getElementById('modal-new-employee').classList.remove('hidden');
        }
        function openNewItemModal() {
            document.getElementById('modal-new-item').classList.remove('hidden');
        }
        function closeModal(modalId) {
            document.getElementById(modalId).classList.add('hidden');
        }

        function populateEmployeeDropdown() {
            const select = document.getElementById('ord-employee');
            select.innerHTML = '';
            state.employees.forEach(emp => {
                let opt = document.createElement('option');
                opt.value = emp.name;
                opt.textContent = `${emp.name} (${emp.role})`;
                select.appendChild(opt);
            });
        }

        // Calculations for New Order
        function calculateAdvanceAndProfit() {
            const price = parseFloat(document.getElementById('ord-price').value) || 0;
            const expense = parseFloat(document.getElementById('ord-expense').value) || 0;
            const stitchCharge = parseFloat(document.getElementById('ord-stitch-charge').value) || 0;

            const advance = price / 2;
            document.getElementById('ord-advance').value = advance;

            const remainingAdvance = advance - expense;
            const hintElem = document.getElementById('advance-hint');
            hintElem.innerText = `Remaining Advance after Expense: ₹${remainingAdvance}`;
            if(remainingAdvance < 0) {
                hintElem.className = "text-xs text-red-400 mt-1";
            } else {
                hintElem.className = "text-xs text-emerald-400 mt-1";
            }

            // Profit = Total Price - (Expense + Stitching Charge)
            const profit = price - (expense + stitchCharge);
            document.getElementById('ord-calculated-profit').innerText = `₹${profit}`;
        }

        // Save New Order
        function handleSaveOrder(e) {
            e.preventDefault();
            const price = parseFloat(document.getElementById('ord-price').value);
            const expense = parseFloat(document.getElementById('ord-expense').value);
            const stitchCharge = parseFloat(document.getElementById('ord-stitch-charge').value);
            
            const newOrder = {
                id: Date.now(),
                customer: document.getElementById('ord-customer').value,
                whatsapp: document.getElementById('ord-whatsapp').value,
                platform: document.getElementById('ord-platform').value,
                dress: document.getElementById('ord-dress').value,
                date: document.getElementById('ord-date').value,
                price: price,
                advance: price / 2,
                expense: expense,
                employee: document.getElementById('ord-employee').value,
                stitchCharge: stitchCharge,
                profit: price - (expense + stitchCharge),
                status: 'Pending'
            };

            state.orders.push(newOrder);
            saveData();
            closeModal('modal-new-order');
        }

        // Save New Employee
        function handleSaveEmployee(e) {
            e.preventDefault();
            const newEmp = {
                id: Date.now(),
                name: document.getElementById('emp-name').value,
                role: document.getElementById('emp-role').value
            };
            state.employees.push(newEmp);
            saveData();
            closeModal('modal-new-employee');
        }

        // Image Validator (Max 5MB)
        function validateImageSize(input) {
            if (input.files && input.files[0]) {
                const fileSize = input.files[0].size / 1024 / 1024; // in MB
                if (fileSize > 5) {
                    alert('File size exceeds 5MB limit. Please choose a smaller image.');
                    input.value = '';
                }
            }
        }

        // Save Store Item
        function handleSaveItem(e) {
            e.preventDefault();
            const title = document.getElementById('item-title').value;
            const fileInput = document.getElementById('item-image');
            
            if (fileInput.files && fileInput.files[0]) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    state.items.push({
                        id: Date.now(),
                        title: title,
                        image: e.target.result
                    });
                    saveData();
                    closeModal('modal-new-item');
                };
                reader.readAsDataURL(fileInput.files[0]);
            }
        }

        // Mark Order Completed
        function completeOrder(id) {
            const order = state.orders.find(o => o.id === id);
            if(order) {
                order.status = 'Completed';
                order.completedDate = new Date().toISOString().split('T')[0];
                saveData();
            }
        }

        // Render Dashboard Metrics & Lists
        function refreshUI() {
            let totalRev = 0, totalProf = 0;
            let babyRev = 0, babyProf = 0;
            let ladyRev = 0, ladyProf = 0;
            let completedCount = 0, pendingCount = 0;

            state.orders.forEach(o => {
                if(o.status === 'Completed') {
                    completedCount++;
                    totalRev += o.price;
                    totalProf += o.profit;
                    if(o.platform === 'Baby') { babyRev += o.price; babyProf += o.profit; }
                    if(o.platform === 'Lady') { ladyRev += o.price; ladyProf += o.profit; }
                } else {
                    pendingCount++;
                }
            });

            document.getElementById('dash-total-revenue').innerText = `₹${totalRev}`;
            document.getElementById('dash-total-profit').innerText = `₹${totalProf}`;
            document.getElementById('dash-baby-rev').innerText = `₹${babyRev}`;
            document.getElementById('dash-baby-prof').innerText = `₹${babyProf}`;
            document.getElementById('dash-lady-rev').innerText = `₹${ladyRev}`;
            document.getElementById('dash-lady-prof').innerText = `₹${ladyProf}`;
            document.getElementById('dash-completed-count').innerText = completedCount;
            document.getElementById('dash-pending-count').innerText = pendingCount;

            // Render Active Orders Table
            let activeHtml = '';
            let pendingOrdersList = state.orders.filter(o => o.status === 'Pending');
            if(pendingOrdersList.length === 0) {
                activeHtml = `<tr><td colspan="5" class="p-4 text-center text-slate-500">No active pending orders in queue.</td></tr>`;
            } else {
                pendingOrdersList.forEach(o => {
                    activeHtml += `
                        <tr class="hover:bg-slate-900/50">
                            <td class="p-3 font-medium text-white">${o.customer}<br><span class="text-xs text-slate-400"><i class="fa-brands fa-whatsapp text-emerald-400"></i> ${o.whatsapp}</span></td>
                            <td class="p-3"><span class="px-2 py-0.5 rounded text-xs font-semibold ${o.platform==='Baby'?'bg-pink-950 text-pink-300':'bg-red-950 text-red-300'}">${o.platform}</span> - ${o.dress}</td>
                            <td class="p-3 text-slate-300">${o.date}</td>
                            <td class="p-3 text-slate-300">${o.employee}</td>
                            <td class="p-3">
                                <button onclick="completeOrder(${o.id})" class="bg-emerald-700 hover:bg-emerald-800 text-white px-3 py-1 rounded text-xs font-semibold shadow flex items-center space-x-1">
                                    <i class="fa-solid fa-check"></i><span>Complete</span>
                                </button>
                            </td>
                        </tr>
                    `;
                });
            }
            document.getElementById('active-orders-table').innerHTML = activeHtml;

            // Render Customers Table
            renderCustomersTable();
            // Render Completed Archive
            renderCompletedArchive();
            // Render Employees
            renderEmployees();
            // Render Store Items
            renderStoreItems();
        }

        function renderCustomersTable() {
            // Group by customer name
            let custMap = {};
            state.orders.forEach(o => {
                if(!custMap[o.customer]) {
                    custMap[o.customer] = { name: o.customer, whatsapp: o.whatsapp, ordersCount: 0, totalPaid: 0, totalProfit: 0 };
                }
                custMap[o.customer].ordersCount++;
                if(o.status === 'Completed') {
                    custMap[o.customer].totalPaid += o.price;
                    custMap[o.customer].totalProfit += o.profit;
                }
            });

            let html = '';
            let customers = Object.values(custMap);
            if(customers.length === 0) {
                html = `<tr><td colspan="6" class="p-4 text-center text-slate-500">No customer data available.</td></tr>`;
            } else {
                customers.forEach(c => {
                    html += `
                        <tr class="hover:bg-slate-900/50 cursor-pointer" onclick="openCustomerProfile('${c.name}')">
                            <td class="p-3 font-medium text-white">${c.name}</td>
                            <td class="p-3 text-slate-300">${c.whatsapp}</td>
                            <td class="p-3 text-slate-300">${c.ordersCount}</td>
                            <td class="p-3 text-blue-400 font-semibold">₹${c.totalPaid}</td>
                            <td class="p-3 text-emerald-400 font-semibold">₹${c.totalProfit}</td>
                            <td class="p-3"><span class="text-xs text-blue-400 underline">View Profile</span></td>
                        </tr>
                    `;
                });
            }
            document.getElementById('customers-table').innerHTML = html;
        }

        function openCustomerProfile(custName) {
            document.getElementById('profile-cust-name').innerText = `${custName}'s Profile`;
            let custOrders = state.orders.filter(o => o.customer === custName);
            let totalOrders = custOrders.length;
            let totalCash = 0, totalProfit = 0;
            
            let listHtml = '';
            custOrders.forEach(o => {
                if(o.status === 'Completed') {
                    totalCash += o.price;
                    totalProfit += o.profit;
                }
                listHtml += `
                    <tr>
                        <td class="p-2.5">${o.dress} (${o.platform})</td>
                        <td class="p-2.5">${o.date}</td>
                        <td class="p-2.5 text-blue-400">₹${o.price}</td>
                        <td class="p-2.5 text-emerald-400">₹${o.profit}</td>
                        <td class="p-2.5"><span class="px-2 py-0.5 rounded text-[10px] font-semibold ${o.status==='Completed'?'bg-emerald-950 text-emerald-300':'bg-amber-950 text-amber-300'}">${o.status}</span></td>
                    </tr>
                `;
            });

            document.getElementById('profile-total-orders').innerText = totalOrders;
            document.getElementById('profile-total-cash').innerText = `₹${totalCash}`;
            document.getElementById('profile-total-profit').innerText = `₹${totalProfit}`;
            document.getElementById('profile-orders-list').innerHTML = listHtml;
            document.getElementById('modal-customer-profile').classList.remove('hidden');
        }

        function renderCompletedArchive() {
            let html = '';
            let completed = state.orders.filter(o => o.status === 'Completed');
            if(completed.length === 0) {
                html = `<tr><td colspan="5" class="p-4 text-center text-slate-500">No completed orders archive.</td></tr>`;
            } else {
                completed.forEach(o => {
                    html += `
                        <tr class="hover:bg-slate-900/50">
                            <td class="p-3 font-medium text-white">${o.customer}</td>
                            <td class="p-3">${o.dress} <span class="text-xs text-slate-400">(${o.platform})</span></td>
                            <td class="p-3 text-blue-400">₹${o.price}</td>
                            <td class="p-3 text-emerald-400">₹${o.profit}</td>
                            <td class="p-3 text-slate-300 text-xs">${o.completedDate || 'N/A'}</td>
                        </tr>
                    `;
                });
            }
            document.getElementById('completed-orders-table').innerHTML = html;
        }

        function renderEmployees() {
            let html = '';
            state.employees.forEach(emp => {
                html += `
                    <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl flex items-center justify-between shadow">
                        <div>
                            <h4 class="font-bold text-white">${emp.name}</h4>
                            <p class="text-xs text-slate-400 mt-0.5"><i class="fa-solid fa-scissors text-red-400 mr-1"></i> ${emp.role}</p>
                        </div>
                        <div class="bg-red-950/60 p-2.5 rounded-lg text-red-400">
                            <i class="fa-solid fa-user-check"></i>
                        </div>
                    </div>
                `;
            });
            document.getElementById('employees-grid').innerHTML = html;
        }

        function renderStoreItems() {
            let html = '';
            if(state.items.length === 0) {
                html = `<div class="col-span-full p-8 text-center text-slate-500 bg-slate-900 rounded-xl border border-slate-800">No items uploaded in store catalog yet.</div>`;
            } else {
                state.items.forEach(item => {
                    html += `
                        <div class="bg-slate-900 border border-slate-800 rounded-xl overflow-hidden shadow group">
                            <div class="h-48 overflow-hidden bg-slate-950 flex items-center justify-center">
                                <img src="${item.image}" alt="${item.title}" class="w-full h-full object-cover group-hover:scale-105 transition duration-300">
                            </div>
                            <div class="p-3">
                                <h4 class="font-bold text-white text-sm truncate">${item.title}</h4>
                                <span class="text-[10px] text-slate-400 uppercase tracking-wider">Catalog Item</span>
                            </div>
                        </div>
                    `;
                });
            }
            document.getElementById('item-store-grid').innerHTML = html;
        }

        function renderReports() {
            let filter = document.getElementById('report-month-filter').value;
            let rev = 0, prof = 0, totalOrders = state.orders.length, completedOrders = 0;

            state.orders.forEach(o => {
                if(o.status === 'Completed') {
                    completedOrders++;
                    rev += o.price;
                    prof += o.profit;
                }
            });

            document.getElementById('rep-revenue').innerText = `₹${rev}`;
            document.getElementById('rep-profit').innerText = `₹${prof}`;
            document.getElementById('rep-total-orders').innerText = totalOrders;
            
            let rate = totalOrders > 0 ? Math.round((completedOrders / totalOrders) * 100) : 0;
            document.getElementById('rep-completion-rate').innerText = `${rate}%`;
        }

        // Initial Load Run
        refreshUI();
    </script>
</body>
</html>
