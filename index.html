import React, { useState, useMemo } from 'react';
import {
  Wallet,
  CreditCard,
  Plus,
  ArrowDownCircle,
  ArrowUpCircle,
  List,
  Home,
  X,
  PiggyBank,
  Settings,
  Landmark,
  Calendar,
  Edit2
} from 'lucide-react';

// --- 初期データ ---
const INITIAL_ACCOUNTS = [
  { id: '1', name: 'お財布 (現金)', type: 'wallet', initialBalance: 15000 },
  { id: '2', name: 'メインカード', type: 'creditCard', limitAmount: 300000 },
  { id: '3', name: '〇〇銀行', type: 'bank', initialBalance: 100000 },
];

const EXPENSE_CATEGORIES = [
  { id: 'e1', name: '食費', icon: '🍽️' },
  { id: 'e2', name: '日用品', icon: '🧴' },
  { id: 'e3', name: '交通費', icon: '🚃' },
  { id: 'e4', name: '交際費', icon: '🍻' },
  { id: 'e5', name: 'エンタメ', icon: '🎬' },
  { id: 'e6', name: 'その他', icon: '📦' },
];

const INCOME_CATEGORIES = [
  { id: 'i1', name: '給与', icon: '💼' },
  { id: 'i2', name: 'お小遣い', icon: '💰' },
  { id: 'i3', name: '立替返金', icon: '🔄' },
  { id: 'i4', name: 'その他', icon: '🎉' },
];

const getAccountIcon = (type) => {
  switch (type) {
    case 'wallet': return <Wallet className="w-5 h-5" />;
    case 'creditCard': return <CreditCard className="w-5 h-5" />;
    case 'bank': return <Landmark className="w-5 h-5" />;
    default: return <PiggyBank className="w-5 h-5" />;
  }
};

export default function App() {
  // --- 状態管理 ---
  const [accounts, setAccounts] = useState(INITIAL_ACCOUNTS);
  const [transactions, setTransactions] = useState([]);
  const [currentTab, setCurrentTab] = useState('home');
  const [isTxModalOpen, setIsTxModalOpen] = useState(false);
  const [isAccountModalOpen, setIsAccountModalOpen] = useState(false);
  const [editingAccount, setEditingAccount] = useState(null); // 編集対象のアカウントを保持する状態

  // --- 計算ロジック ---
  const currentMonthPrefix = useMemo(() => new Date().toISOString().slice(0, 7), []);
  const currentMonthDisplay = useMemo(() => new Date().getMonth() + 1, []);

  const accountStats = useMemo(() => {
    const stats = {};
    accounts.forEach(acc => {
      if (acc.type === 'creditCard') {
        stats[acc.id] = { type: 'creditCard', limitAmount: acc.limitAmount || 0, usedThisMonth: 0 };
      } else {
        stats[acc.id] = { type: acc.type, balance: acc.initialBalance || 0 };
      }
    });

    transactions.forEach(tx => {
      const stat = stats[tx.accountId];
      if (!stat) return;

      if (stat.type === 'creditCard') {
        if (tx.date.startsWith(currentMonthPrefix)) {
          if (tx.type === 'expense') {
            stat.usedThisMonth += tx.amount;
          } else {
            stat.usedThisMonth -= tx.amount;
          }
        }
      } else {
        if (tx.type === 'income') {
          stat.balance += tx.amount;
        } else {
          stat.balance -= tx.amount;
        }
      }
    });
    return stats;
  }, [accounts, transactions, currentMonthPrefix]);

  const totalBalance = useMemo(() => {
    return Object.values(accountStats).reduce((sum, stat) => {
      if (stat.type === 'creditCard') {
        return sum - stat.usedThisMonth; 
      } else {
        return sum + stat.balance;
      }
    }, 0);
  }, [accountStats]);

  const sortedTransactions = useMemo(() => {
    return [...transactions].sort((a, b) => new Date(b.date) - new Date(a.date));
  }, [transactions]);

  // --- ハンドラー ---
  const handleAddTransaction = (tx) => {
    setTransactions([{ ...tx, id: Date.now().toString() }, ...transactions]);
    setIsTxModalOpen(false);
  };

  const handleSaveAccount = (accountData) => {
    if (editingAccount) {
      // 既存アカウントの更新
      setAccounts(accounts.map(acc => 
        acc.id === editingAccount.id ? { ...acc, ...accountData } : acc
      ));
    } else {
      // 新規アカウントの追加
      setAccounts([...accounts, { ...accountData, id: Date.now().toString() }]);
    }
    closeAccountModal();
  };

  const openEditAccountModal = (account) => {
    setEditingAccount(account);
    setIsAccountModalOpen(true);
  };

  const openAddAccountModal = () => {
    setEditingAccount(null);
    setIsAccountModalOpen(true);
  };

  const closeAccountModal = () => {
    setIsAccountModalOpen(false);
    setEditingAccount(null);
  };

  // --- フォーマット ---
  const formatCurrency = (amount) => {
    return new Intl.NumberFormat('ja-JP', { style: 'currency', currency: 'JPY' }).format(amount);
  };

  return (
    <div className="flex justify-center bg-gray-100 min-h-screen font-sans">
      <div className="w-full max-w-md bg-white shadow-xl relative flex flex-col h-screen overflow-hidden">
        
        {/* ヘッダー */}
        <header className="bg-indigo-600 text-white p-5 rounded-b-2xl shadow-md z-10 shrink-0">
          <h1 className="text-lg font-semibold mb-1">
            {currentTab === 'home' && 'ホーム'}
            {currentTab === 'history' && '履歴'}
            {currentTab === 'settings' && 'アカウント管理'}
          </h1>
          {currentTab === 'home' && (
            <div>
              <p className="text-indigo-200 text-sm">総資産残高</p>
              <p className="text-3xl font-bold tracking-tight">{formatCurrency(totalBalance)}</p>
            </div>
          )}
        </header>

        {/* メインコンテンツ */}
        <main className="flex-1 overflow-y-auto p-4 pb-24">
          
          {/* ホームタブ */}
          {currentTab === 'home' && (
            <div className="space-y-6">
              {/* アカウント別残高 */}
              <section>
                <div className="flex justify-between items-center mb-3 ml-1">
                  <h2 className="text-sm font-bold text-gray-500">アカウント別残高</h2>
                  <div className="text-xs text-indigo-500 bg-indigo-50 px-2 py-1 rounded flex items-center">
                    <Calendar className="w-3 h-3 mr-1" />
                    {currentMonthDisplay}月の利用状況
                  </div>
                </div>
                
                <div className="space-y-3">
                  {accounts.map(acc => {
                    const stat = accountStats[acc.id];
                    
                    // クレジットカードの表示
                    if (acc.type === 'creditCard') {
                      const available = stat.limitAmount - stat.usedThisMonth;
                      const usagePercent = Math.min(100, Math.max(0, (stat.usedThisMonth / stat.limitAmount) * 100)) || 0;
                      
                      return (
                        <div key={acc.id} className="bg-white p-4 rounded-xl flex flex-col border border-gray-200 shadow-sm">
                          <div className="flex items-center justify-between mb-2">
                            <div className="flex items-center space-x-3">
                              <div className="p-2 rounded-lg bg-blue-100 text-blue-600">
                                {getAccountIcon(acc.type)}
                              </div>
                              <span className="font-medium text-gray-800">{acc.name}</span>
                            </div>
                            <div className="text-right">
                              <div className="text-[10px] text-gray-400 font-medium">利用可能枠</div>
                              <span className={`font-semibold ${available < 0 ? 'text-red-500' : 'text-gray-900'}`}>
                                {formatCurrency(available)}
                              </span>
                            </div>
                          </div>
                          <div className="w-full bg-gray-100 rounded-full h-1.5 mt-2 overflow-hidden">
                            <div 
                              className={`h-1.5 rounded-full transition-all duration-500 ${usagePercent > 80 ? 'bg-red-500' : 'bg-blue-500'}`} 
                              style={{ width: `${usagePercent}%` }}
                            ></div>
                          </div>
                          <div className="text-[10px] text-gray-500 mt-1.5 text-right flex justify-between">
                            <span>{currentMonthDisplay}月利用分</span>
                            <span>{formatCurrency(stat.usedThisMonth)} / 上限 {formatCurrency(stat.limitAmount)}</span>
                          </div>
                        </div>
                      );
                    }
                    
                    // 現金・銀行の表示
                    return (
                      <div key={acc.id} className="bg-white p-4 rounded-xl flex items-center justify-between border border-gray-200 shadow-sm">
                        <div className="flex items-center space-x-3">
                          <div className={`p-2 rounded-lg ${
                            acc.type === 'wallet' ? 'bg-orange-100 text-orange-600' : 'bg-emerald-100 text-emerald-600'
                          }`}>
                            {getAccountIcon(acc.type)}
                          </div>
                          <span className="font-medium text-gray-800">{acc.name}</span>
                        </div>
                        <span className={`font-semibold ${stat.balance < 0 ? 'text-red-500' : 'text-gray-900'}`}>
                          {formatCurrency(stat.balance)}
                        </span>
                      </div>
                    );
                  })}
                </div>
              </section>

              {/* 最近の取引 */}
              <section>
                <div className="flex justify-between items-end mb-3 ml-1">
                  <h2 className="text-sm font-bold text-gray-500">最近の記録</h2>
                  <button onClick={() => setCurrentTab('history')} className="text-xs text-indigo-600 font-medium">すべて見る</button>
                </div>
                <div className="bg-white border border-gray-100 rounded-xl shadow-sm overflow-hidden">
                  {sortedTransactions.length === 0 ? (
                    <div className="p-6 text-center text-gray-400 text-sm">
                      まだ記録がありません。<br/>右下の「＋」から追加しましょう。
                    </div>
                  ) : (
                    <div className="divide-y divide-gray-50">
                      {sortedTransactions.slice(0, 5).map(tx => (
                        <TransactionItem key={tx.id} tx={tx} accounts={accounts} formatCurrency={formatCurrency} />
                      ))}
                    </div>
                  )}
                </div>
              </section>
            </div>
          )}

          {/* 履歴タブ */}
          {currentTab === 'history' && (
            <div className="space-y-4">
               {sortedTransactions.length === 0 ? (
                    <div className="text-center text-gray-400 text-sm mt-10">
                      履歴がありません。
                    </div>
                  ) : (
                    <div className="bg-white border border-gray-100 rounded-xl shadow-sm overflow-hidden divide-y divide-gray-50">
                      {sortedTransactions.map(tx => (
                         <TransactionItem key={tx.id} tx={tx} accounts={accounts} formatCurrency={formatCurrency} />
                      ))}
                    </div>
               )}
            </div>
          )}

          {/* 設定（アカウント管理）タブ */}
          {currentTab === 'settings' && (
            <div className="space-y-4">
               <p className="text-sm text-gray-500 mb-4">アカウントの追加や、残高・上限額の修正ができます。</p>
               <div className="space-y-3">
                  {accounts.map(acc => (
                    <div key={acc.id} className="bg-white p-4 rounded-xl flex items-center justify-between border border-gray-100 shadow-sm">
                      <div className="flex items-center space-x-3">
                        <div className={`p-2 rounded-lg ${
                          acc.type === 'wallet' ? 'bg-orange-100 text-orange-600' :
                          acc.type === 'creditCard' ? 'bg-blue-100 text-blue-600' :
                          'bg-emerald-100 text-emerald-600'
                        }`}>
                          {getAccountIcon(acc.type)}
                        </div>
                        <div>
                           <div className="font-medium text-gray-800">{acc.name}</div>
                           <div className="text-xs text-gray-400 mt-0.5">
                             {acc.type === 'creditCard' 
                               ? `上限額: ${formatCurrency(acc.limitAmount)}` 
                               : `初期残高: ${formatCurrency(acc.initialBalance)}`}
                           </div>
                        </div>
                      </div>
                      
                      {/* 編集ボタン */}
                      <button 
                        onClick={() => openEditAccountModal(acc)}
                        className="p-2 text-gray-400 hover:text-indigo-600 hover:bg-indigo-50 rounded-lg transition-colors"
                        aria-label="編集"
                      >
                        <Edit2 className="w-5 h-5" />
                      </button>
                    </div>
                  ))}
                </div>
                <button 
                  onClick={openAddAccountModal}
                  className="w-full py-3 mt-4 border-2 border-dashed border-gray-300 text-gray-500 rounded-xl font-medium hover:bg-gray-50 transition-colors flex items-center justify-center space-x-2"
                >
                  <Plus className="w-4 h-4" />
                  <span>アカウントを追加する</span>
                </button>
            </div>
          )}
        </main>

        {/* FAB (Floating Action Button) */}
        {currentTab !== 'settings' && (
          <button
            onClick={() => setIsTxModalOpen(true)}
            className="absolute bottom-20 right-6 bg-indigo-600 hover:bg-indigo-700 text-white p-4 rounded-full shadow-lg shadow-indigo-200 transition-transform active:scale-95 z-20"
          >
            <Plus className="w-6 h-6" />
          </button>
        )}

        {/* ボトムナビゲーション */}
        <nav className="absolute bottom-0 w-full bg-white border-t border-gray-100 flex justify-around pb-safe pt-2 px-2 z-10 text-xs text-gray-500 shrink-0">
          <button 
            onClick={() => setCurrentTab('home')} 
            className={`flex flex-col items-center p-2 w-full ${currentTab === 'home' ? 'text-indigo-600' : 'hover:text-gray-800'}`}
          >
            <Home className="w-6 h-6 mb-1" />
            ホーム
          </button>
          <button 
            onClick={() => setCurrentTab('history')} 
            className={`flex flex-col items-center p-2 w-full ${currentTab === 'history' ? 'text-indigo-600' : 'hover:text-gray-800'}`}
          >
            <List className="w-6 h-6 mb-1" />
            履歴
          </button>
          <button 
            onClick={() => setCurrentTab('settings')} 
            className={`flex flex-col items-center p-2 w-full ${currentTab === 'settings' ? 'text-indigo-600' : 'hover:text-gray-800'}`}
          >
            <Settings className="w-6 h-6 mb-1" />
            アカウント
          </button>
        </nav>

        {isTxModalOpen && (
          <TransactionModal 
            onClose={() => setIsTxModalOpen(false)} 
            onSave={handleAddTransaction}
            accounts={accounts}
          />
        )}

        {isAccountModalOpen && (
          <AccountModal
            onClose={closeAccountModal}
            onSave={handleSaveAccount}
            initialData={editingAccount} // 編集対象のデータを渡す
          />
        )}
      </div>
    </div>
  );
}

// --- サブコンポーネント ---

function TransactionItem({ tx, accounts, formatCurrency }) {
  const account = accounts.find(a => a.id === tx.accountId);
  const isIncome = tx.type === 'income';
  
  let categoryIcon = '📝';
  let categoryName = '未分類';
  if (isIncome) {
    const cat = INCOME_CATEGORIES.find(c => c.id === tx.categoryId);
    if(cat) { categoryIcon = cat.icon; categoryName = cat.name; }
  } else {
    const cat = EXPENSE_CATEGORIES.find(c => c.id === tx.categoryId);
    if(cat) { categoryIcon = cat.icon; categoryName = cat.name; }
  }

  const date = new Date(tx.date);
  const formattedDate = `${date.getMonth() + 1}/${date.getDate()}`;

  return (
    <div className="p-4 flex items-center justify-between">
      <div className="flex items-center space-x-4">
        <div className="text-2xl bg-gray-50 w-12 h-12 rounded-full flex items-center justify-center shrink-0">
          {categoryIcon}
        </div>
        <div className="min-w-0">
          <p className="font-medium text-gray-800 leading-tight truncate">{categoryName}</p>
          <div className="flex items-center text-xs text-gray-500 mt-1 space-x-2">
            <span>{formattedDate}</span>
            <span className="w-1 h-1 bg-gray-300 rounded-full"></span>
            <span className="truncate">{account?.name || '不明なアカウント'}</span>
          </div>
          {tx.note && <p className="text-xs text-gray-400 mt-1 truncate max-w-[200px]">{tx.note}</p>}
        </div>
      </div>
      <div className={`font-semibold shrink-0 ml-2 ${isIncome ? 'text-emerald-600' : 'text-gray-800'}`}>
        {isIncome ? '+' : '-'}{formatCurrency(tx.amount)}
      </div>
    </div>
  );
}

function TransactionModal({ onClose, onSave, accounts }) {
  const [type, setType] = useState('expense');
  const [amount, setAmount] = useState('');
  const [accountId, setAccountId] = useState(accounts[0]?.id || '');
  const [categoryId, setCategoryId] = useState(EXPENSE_CATEGORIES[0].id);
  const [date, setDate] = useState(new Date().toISOString().split('T')[0]);
  const [note, setNote] = useState('');

  const handleTypeChange = (newType) => {
    setType(newType);
    setCategoryId(newType === 'expense' ? EXPENSE_CATEGORIES[0].id : INCOME_CATEGORIES[0].id);
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    if (!amount || isNaN(amount) || amount <= 0) return;
    
    const finalAccountId = accountId || accounts[0]?.id;
    if(!finalAccountId) return;

    onSave({
      type,
      amount: parseInt(amount, 10),
      accountId: finalAccountId,
      categoryId,
      date,
      note
    });
  };

  const currentCategories = type === 'expense' ? EXPENSE_CATEGORIES : INCOME_CATEGORIES;

  return (
    <div className="absolute inset-0 bg-black/40 z-30 flex items-end justify-center sm:items-center p-0 sm:p-4 animate-in fade-in duration-200">
      <div className="bg-white w-full h-[90%] sm:h-auto sm:max-h-[90%] sm:rounded-2xl rounded-t-2xl shadow-2xl flex flex-col animate-in slide-in-from-bottom-4 duration-300">
        
        <div className="flex justify-between items-center p-4 border-b border-gray-100 shrink-0">
          <h2 className="text-lg font-bold text-gray-800">記録を追加</h2>
          <button onClick={onClose} className="p-2 text-gray-400 hover:text-gray-600 rounded-full hover:bg-gray-100">
            <X className="w-6 h-6" />
          </button>
        </div>

        <div className="overflow-y-auto flex-1 p-5">
          <div className="flex p-1 bg-gray-100 rounded-xl mb-6">
            <button
              type="button"
              onClick={() => handleTypeChange('expense')}
              className={`flex-1 py-2 text-sm font-medium rounded-lg flex items-center justify-center space-x-1 transition-colors ${
                type === 'expense' ? 'bg-white text-red-600 shadow-sm' : 'text-gray-500'
              }`}
            >
              <ArrowDownCircle className="w-4 h-4" />
              <span>支出</span>
            </button>
            <button
              type="button"
              onClick={() => handleTypeChange('income')}
              className={`flex-1 py-2 text-sm font-medium rounded-lg flex items-center justify-center space-x-1 transition-colors ${
                type === 'income' ? 'bg-white text-emerald-600 shadow-sm' : 'text-gray-500'
              }`}
            >
              <ArrowUpCircle className="w-4 h-4" />
              <span>収入</span>
            </button>
          </div>

          <form id="tx-form" onSubmit={handleSubmit} className="space-y-5">
            <div>
              <label className="block text-xs font-semibold text-gray-500 mb-1">金額</label>
              <div className="relative">
                <span className="absolute left-4 top-1/2 -translate-y-1/2 text-gray-400 font-bold">¥</span>
                <input
                  type="number"
                  required
                  value={amount}
                  onChange={(e) => setAmount(e.target.value)}
                  className="w-full pl-10 pr-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:bg-white text-xl font-bold text-gray-800"
                  placeholder="0"
                  pattern="\d*"
                />
              </div>
            </div>

            {accounts.length > 0 ? (
              <div>
                <label className="block text-xs font-semibold text-gray-500 mb-1">アカウント（財布・カード）</label>
                <select
                  value={accountId}
                  onChange={(e) => setAccountId(e.target.value)}
                  className="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:bg-white text-gray-800"
                >
                  {accounts.map(acc => (
                    <option key={acc.id} value={acc.id}>{acc.name}</option>
                  ))}
                </select>
              </div>
            ) : (
              <div className="text-sm text-red-500 p-3 bg-red-50 rounded-xl">
                先にアカウント（財布など）を登録してください。
              </div>
            )}

            <div>
              <label className="block text-xs font-semibold text-gray-500 mb-1">カテゴリー</label>
              <div className="grid grid-cols-4 gap-2">
                {currentCategories.map(cat => (
                  <button
                    key={cat.id}
                    type="button"
                    onClick={() => setCategoryId(cat.id)}
                    className={`flex flex-col items-center justify-center p-3 rounded-xl border transition-all ${
                      categoryId === cat.id 
                        ? `border-${type === 'expense' ? 'red' : 'emerald'}-500 bg-${type === 'expense' ? 'red' : 'emerald'}-50` 
                        : 'border-gray-200 bg-white hover:bg-gray-50'
                    }`}
                  >
                    <span className="text-2xl mb-1">{cat.icon}</span>
                    <span className="text-[10px] font-medium text-gray-600">{cat.name}</span>
                  </button>
                ))}
              </div>
            </div>

            <div>
              <label className="block text-xs font-semibold text-gray-500 mb-1">日付</label>
              <input
                type="date"
                required
                value={date}
                onChange={(e) => setDate(e.target.value)}
                className="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:bg-white text-gray-800"
              />
            </div>

            <div>
              <label className="block text-xs font-semibold text-gray-500 mb-1">メモ（任意）</label>
              <input
                type="text"
                value={note}
                onChange={(e) => setNote(e.target.value)}
                className="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:bg-white text-gray-800"
                placeholder="例: スーパーでの買い物"
              />
            </div>
          </form>
        </div>

        <div className="p-4 border-t border-gray-100 bg-white pb-safe shrink-0">
          <button
            type="submit"
            form="tx-form"
            disabled={!amount || accounts.length === 0}
            className="w-full py-4 bg-indigo-600 text-white rounded-xl font-bold text-lg disabled:opacity-50 disabled:cursor-not-allowed hover:bg-indigo-700 active:scale-[0.98] transition-transform shadow-lg shadow-indigo-200"
          >
            保存する
          </button>
        </div>
      </div>
    </div>
  );
}

// アカウント追加・編集モーダル
function AccountModal({ onClose, onSave, initialData }) {
  // initialData があれば編集モード、なければ新規追加モード
  const isEditMode = !!initialData;
  
  const [name, setName] = useState(initialData?.name || '');
  const [type, setType] = useState(initialData?.type || 'wallet');
  
  // 初期値のセット（クレカならlimitAmount、その他はinitialBalance）
  const [amountValue, setAmountValue] = useState(
    initialData 
      ? (initialData.type === 'creditCard' ? initialData.limitAmount?.toString() : initialData.initialBalance?.toString())
      : ''
  );

  const handleSubmit = (e) => {
    e.preventDefault();
    if (!name.trim()) return;

    const parsedAmount = amountValue ? parseInt(amountValue, 10) : 0;
    
    onSave({
      name: name.trim(),
      type,
      ...(type === 'creditCard' ? { limitAmount: parsedAmount } : { initialBalance: parsedAmount })
    });
  };

  return (
    <div className="absolute inset-0 bg-black/40 z-30 flex items-end justify-center sm:items-center p-0 sm:p-4 animate-in fade-in duration-200">
      <div className="bg-white w-full sm:w-96 sm:rounded-2xl rounded-t-2xl shadow-2xl flex flex-col animate-in slide-in-from-bottom-4 duration-300">
        
        <div className="flex justify-between items-center p-4 border-b border-gray-100">
          <h2 className="text-lg font-bold text-gray-800">
            {isEditMode ? 'アカウントを編集' : 'アカウントを追加'}
          </h2>
          <button onClick={onClose} className="p-2 text-gray-400 hover:text-gray-600 rounded-full hover:bg-gray-100">
            <X className="w-6 h-6" />
          </button>
        </div>

        <div className="p-5">
          <form id="account-form" onSubmit={handleSubmit} className="space-y-5">
            
            <div>
              <label className="block text-xs font-semibold text-gray-500 mb-1">アカウント名</label>
              <input
                type="text"
                required
                value={name}
                onChange={(e) => setName(e.target.value)}
                className="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:bg-white text-gray-800"
                placeholder={type === 'creditCard' ? "例: 楽天カード" : "例: サブのお財布"}
              />
            </div>

            <div>
              <label className="block text-xs font-semibold text-gray-500 mb-2">種類</label>
              <div className="grid grid-cols-3 gap-2">
                <button
                  type="button"
                  onClick={() => setType('wallet')}
                  className={`flex flex-col items-center justify-center p-3 rounded-xl border transition-all ${
                    type === 'wallet' 
                      ? 'border-orange-500 bg-orange-50 text-orange-600' 
                      : 'border-gray-200 bg-white hover:bg-gray-50 text-gray-500'
                  }`}
                >
                  <Wallet className="w-6 h-6 mb-1" />
                  <span className="text-[10px] font-medium">現金</span>
                </button>
                <button
                  type="button"
                  onClick={() => setType('creditCard')}
                  className={`flex flex-col items-center justify-center p-3 rounded-xl border transition-all ${
                    type === 'creditCard' 
                      ? 'border-blue-500 bg-blue-50 text-blue-600' 
                      : 'border-gray-200 bg-white hover:bg-gray-50 text-gray-500'
                  }`}
                >
                  <CreditCard className="w-6 h-6 mb-1" />
                  <span className="text-[10px] font-medium">カード</span>
                </button>
                <button
                  type="button"
                  onClick={() => setType('bank')}
                  className={`flex flex-col items-center justify-center p-3 rounded-xl border transition-all ${
                    type === 'bank' 
                      ? 'border-emerald-500 bg-emerald-50 text-emerald-600' 
                      : 'border-gray-200 bg-white hover:bg-gray-50 text-gray-500'
                  }`}
                >
                  <Landmark className="w-6 h-6 mb-1" />
                  <span className="text-[10px] font-medium">銀行口座</span>
                </button>
              </div>
            </div>

            <div>
              <label className="block text-xs font-semibold text-gray-500 mb-1">
                {type === 'creditCard' ? '毎月の上限額（利用枠）' : '現在の残高（初期残高）'}
              </label>
              <div className="relative">
                <span className="absolute left-4 top-1/2 -translate-y-1/2 text-gray-400 font-bold">¥</span>
                <input
                  type="number"
                  value={amountValue}
                  onChange={(e) => setAmountValue(e.target.value)}
                  className="w-full pl-10 pr-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:bg-white font-bold text-gray-800"
                  placeholder="0"
                  pattern="\d*"
                />
              </div>
              {type === 'creditCard' && (
                <p className="text-[10px] text-gray-500 mt-1">※設定した上限額は毎月1日にリセット（復活）します。</p>
              )}
            </div>
          </form>
        </div>

        <div className="p-4 border-t border-gray-100 bg-white pb-safe">
          <button
            type="submit"
            form="account-form"
            disabled={!name.trim()}
            className="w-full py-4 bg-indigo-600 text-white rounded-xl font-bold text-lg disabled:opacity-50 disabled:cursor-not-allowed hover:bg-indigo-700 active:scale-[0.98] transition-transform shadow-lg shadow-indigo-200"
          >
            {isEditMode ? '更新する' : '追加する'}
          </button>
        </div>
      </div>
    </div>
  );
}
