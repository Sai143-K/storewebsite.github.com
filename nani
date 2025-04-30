
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Financial Tracker - Indian Rupees</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body {
            background-color: #f0f7ff;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        .transaction-row:hover {
            background-color: #e6f0fd;
            transition: all 0.2s ease;
        }
    </style>
</head>
<body>
    <div class="min-h-screen">
        <!-- Header -->
        <header class="bg-gradient-to-r from-indigo-600 to-indigo-800 text-white py-6 shadow-lg">
            <div class="container mx-auto px-4">
                <h1 class="text-3xl font-bold">Financial Tracker</h1>
                <p class="mt-2 opacity-90">Track your financial transactions in Indian Rupees (₹)</p>
            </div>
        </header>

        <!-- Main Content -->
        <main class="container mx-auto px-4 py-8">
            <!-- Form Section -->
            <div class="bg-white rounded-lg shadow-md p-6 mb-8">
                <h2 id="form-title" class="text-xl font-semibold text-gray-800 mb-4">Add New Transaction</h2>
                <form id="transaction-form" class="space-y-4">
                    <input type="hidden" id="edit-index" value="-1">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="date" class="block text-sm font-medium text-gray-700 mb-1">Date</label>
                            <input type="date" id="date" name="date" required
                                class="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500">
                        </div>
                        <div>
                            <label for="name" class="block text-sm font-medium text-gray-700 mb-1">Name/Description</label>
                            <input type="text" id="name" name="name" placeholder="e.g., Grocery Shopping" required
                                class="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500">
                        </div>
                        <div>
                            <label for="amount" class="block text-sm font-medium text-gray-700 mb-1">Amount (₹)</label>
                            <input type="number" id="amount" name="amount" step="1" placeholder="0" required
                                class="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500">
                        </div>
                        <div>
                            <label for="number" class="block text-sm font-medium text-gray-700 mb-1">Reference Number</label>
                            <input type="text" id="number" name="number" placeholder="e.g., Invoice #12345"
                                class="w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500">
                        </div>
                    </div>
                    <div class="flex justify-end space-x-3">
                        <button type="button" id="cancel-edit" class="hidden bg-gray-500 hover:bg-gray-600 text-white font-medium py-2 px-6 rounded-md transition duration-300 ease-in-out focus:outline-none focus:ring-2 focus:ring-gray-500 focus:ring-opacity-50">
                            Cancel
                        </button>
                        <button type="submit" id="submit-btn" 
                            class="bg-indigo-600 hover:bg-indigo-700 text-white font-medium py-2 px-6 rounded-md transition duration-300 ease-in-out transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-opacity-50">
                            Add Transaction
                        </button>
                    </div>
                </form>
            </div>

            <!-- Summary Section -->
            <div class="bg-white rounded-lg shadow-md p-6 mb-8">
                <h2 class="text-xl font-semibold text-gray-800 mb-4">Financial Summary</h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                    <div class="bg-green-50 p-4 rounded-lg border border-green-200">
                        <p class="text-sm text-green-700 font-medium">Total Income</p>
                        <p id="total-income" class="text-2xl font-bold text-green-600">₹0</p>
                    </div>
                    <div class="bg-red-50 p-4 rounded-lg border border-red-200">
                        <p class="text-sm text-red-700 font-medium">Total Expenses</p>
                        <p id="total-expenses" class="text-2xl font-bold text-red-600">₹0</p>
                    </div>
                    <div class="bg-blue-50 p-4 rounded-lg border border-blue-200">
                        <p class="text-sm text-blue-700 font-medium">Net Balance</p>
                        <p id="net-balance" class="text-2xl font-bold text-blue-600">₹0</p>
                    </div>
                </div>
            </div>

            <!-- Transactions Table -->
            <div class="bg-white rounded-lg shadow-md p-6">
                <div class="flex justify-between items-center mb-4">
                    <h2 class="text-xl font-semibold text-gray-800">Transaction History</h2>
                    <div class="flex space-x-2">
                        <button id="clear-all" class="text-red-600 hover:text-red-800 text-sm font-medium">
                            Clear All
                        </button>
                    </div>
                </div>
                <div class="overflow-x-auto">
                    <table class="min-w-full divide-y divide-gray-200">
                        <thead class="bg-gray-50">
                            <tr>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Date</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Name/Description</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Amount (₹)</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Reference Number</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Actions</th>
                            </tr>
                        </thead>
                        <tbody id="transactions-body" class="bg-white divide-y divide-gray-200">
                            <!-- Transactions will be added here -->
                        </tbody>
                    </table>
                </div>
                <div id="no-transactions" class="text-center py-8 text-gray-500">
                    No transactions yet. Add one above!
                </div>
            </div>
        </main>

        <!-- Footer -->
        <footer class="bg-gray-800 text-white py-6 mt-8">
            <div class="container mx-auto px-4 text-center">
                <p>&copy; 2023 Financial Tracker. All rights reserved.</p>
            </div>
        </footer>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize transactions from localStorage or empty array
            let transactions = JSON.parse(localStorage.getItem('transactions')) || [];
            
            // DOM elements
            const form = document.getElementById('transaction-form');
            const formTitle = document.getElementById('form-title');
            const submitBtn = document.getElementById('submit-btn');
            const cancelEditBtn = document.getElementById('cancel-edit');
            const editIndexInput = document.getElementById('edit-index');
            const transactionsBody = document.getElementById('transactions-body');
            const noTransactionsMsg = document.getElementById('no-transactions');
            const clearAllBtn = document.getElementById('clear-all');
            const totalIncomeEl = document.getElementById('total-income');
            const totalExpensesEl = document.getElementById('total-expenses');
            const netBalanceEl = document.getElementById('net-balance');
            
            // Format amount in Indian Rupees
            function formatIndianRupees(amount) {
                const num = parseFloat(amount);
                return '₹' + num.toLocaleString('en-IN');
            }
            
            // Update financial summary
            function updateSummary() {
                let income = 0;
                let expenses = 0;
                
                transactions.forEach(transaction => {
                    const amount = parseFloat(transaction.amount);
                    if (amount >= 0) {
                        income += amount;
                    } else {
                        expenses += Math.abs(amount);
                    }
                });
                
                const balance = income - expenses;
                
                totalIncomeEl.textContent = formatIndianRupees(income);
                totalExpensesEl.textContent = formatIndianRupees(expenses);
                netBalanceEl.textContent = formatIndianRupees(balance);
                
                // Change color of net balance based on value
                if (balance > 0) {
                    netBalanceEl.className = 'text-2xl font-bold text-green-600';
                } else if (balance < 0) {
                    netBalanceEl.className = 'text-2xl font-bold text-red-600';
                } else {
                    netBalanceEl.className = 'text-2xl font-bold text-blue-600';
                }
            }
            
            // Display transactions
            function renderTransactions() {
                transactionsBody.innerHTML = '';
                
                if (transactions.length === 0) {
                    noTransactionsMsg.style.display = 'block';
                } else {
                    noTransactionsMsg.style.display = 'none';
                    
                    transactions.forEach((transaction, index) => {
                        const row = document.createElement('tr');
                        row.className = 'transaction-row';
                        
                        // Format date for display
                        const dateObj = new Date(transaction.date);
                        const formattedDate = dateObj.toLocaleDateString('en-IN');
                        
                        // Format amount with Indian Rupee symbol
                        const amount = parseFloat(transaction.amount);
                        const formattedAmount = formatIndianRupees(amount);
                        
                        row.innerHTML = `
                            <td class="px-6 py-4 whitespace-nowrap">${formattedDate}</td>
                            <td class="px-6 py-4">${transaction.name}</td>
                            <td class="px-6 py-4 whitespace-nowrap ${amount >= 0 ? 'text-green-600' : 'text-red-600'} font-medium">${formattedAmount}</td>
                            <td class="px-6 py-4">${transaction.number || '-'}</td>
                            <td class="px-6 py-4 whitespace-nowrap">
                                <button class="edit-btn text-blue-600 hover:text-blue-900 mr-3" data-index="${index}">
                                    Edit
                                </button>
                                <button class="delete-btn text-red-600 hover:text-red-900" data-index="${index}">
                                    Delete
                                </button>
                            </td>
                        `;
                        
                        transactionsBody.appendChild(row);
                    });
                    
                    // Add event listeners to action buttons
                    document.querySelectorAll('.delete-btn').forEach(button => {
                        button.addEventListener('click', function() {
                            const index = parseInt(this.getAttribute('data-index'));
                            deleteTransaction(index);
                        });
                    });
                    
                    document.querySelectorAll('.edit-btn').forEach(button => {
                        button.addEventListener('click', function() {
                            const index = parseInt(this.getAttribute('data-index'));
                            editTransaction(index);
                        });
                    });
                }
                
                // Update summary
                updateSummary();
            }
            
            // Add new transaction
            function addTransaction(transaction) {
                transactions.push(transaction);
                saveTransactions();
                renderTransactions();
            }
            
            // Update existing transaction
            function updateTransaction(index, updatedTransaction) {
                transactions[index] = updatedTransaction;
                saveTransactions();
                renderTransactions();
            }
            
            // Delete transaction
            function deleteTransaction(index) {
                if (confirm('Are you sure you want to delete this transaction?')) {
                    transactions.splice(index, 1);
                    saveTransactions();
                    renderTransactions();
                }
            }
            
            // Edit transaction
            function editTransaction(index) {
                const transaction = transactions[index];
                
                // Fill form with transaction data
                document.getElementById('date').value = transaction.date;
                document.getElementById('name').value = transaction.name;
                document.getElementById('amount').value = transaction.amount;
                document.getElementById('number').value = transaction.number || '';
                
                // Update form state
                editIndexInput.value = index;
                formTitle.textContent = 'Edit Transaction';
                submitBtn.textContent = 'Update Transaction';
                cancelEditBtn.classList.remove('hidden');
                
                // Scroll to form
                form.scrollIntoView({ behavior: 'smooth' });
            }
            
            // Reset form to add mode
            function resetForm() {
                form.reset();
                editIndexInput.value = -1;
                formTitle.textContent = 'Add New Transaction';
                submitBtn.textContent = 'Add Transaction';
                cancelEditBtn.classList.add('hidden');
                document.getElementById('date').valueAsDate = new Date();
            }
            
            // Save transactions to localStorage
            function saveTransactions() {
                localStorage.setItem('transactions', JSON.stringify(transactions));
            }
            
            // Form submission
            form.addEventListener('submit', function(e) {
                e.preventDefault();
                
                const transaction = {
                    date: document.getElementById('date').value,
                    name: document.getElementById('name').value,
                    amount: document.getElementById('amount').value,
                    number: document.getElementById('number').value
                };
                
                const editIndex = parseInt(editIndexInput.value);
                
                if (editIndex >= 0) {
                    // Update existing transaction
                    updateTransaction(editIndex, transaction);
                    resetForm();
                } else {
                    // Add new transaction
                    addTransaction(transaction);
                    form.reset();
                    document.getElementById('date').valueAsDate = new Date();
                }
            });
            
            // Cancel edit button
            cancelEditBtn.addEventListener('click', function() {
                resetForm();
            });
            
            // Clear all transactions
            clearAllBtn.addEventListener('click', function() {
                if (transactions.length === 0) {
                    alert('No transactions to clear.');
                    return;
                } 
                
                if (confirm('Are you sure you want to delete all transactions? This cannot be undone.')) {
                    transactions = [];
                    saveTransactions();
                    renderTransactions();
                    resetForm();
                }
            });
            
            // Set default date to today
            document.getElementById('date').valueAsDate = new Date();
            
            // Initial render
            renderTransactions();
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9386649c40ae3e45',t:'MTc0NjAwOTMzMy4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
