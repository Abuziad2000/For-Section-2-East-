import React, { useState, useEffect } from 'react';
import { initializeApp } from 'firebase/app';
import { 
  getFirestore, 
  collection, 
  doc, 
  onSnapshot, 
  setDoc, 
  addDoc, 
  query, 
  orderBy,
  getAuth,
  signInAnonymously,
  signInWithCustomToken,
  onAuthStateChanged
} from 'firebase/firestore';

// إعدادات قاعدة البيانات - تعمل تلقائياً في البيئة السحابية
const firebaseConfig = JSON.parse(__firebase_config);
const app = initializeApp(firebaseConfig);
const db = getFirestore(app);
const auth = getAuth(app);
const appId = typeof __app_id !== 'undefined' ? __app_id : 'latti-community-app';

export default function App() {
  const [user, setUser] = useState(null);
  const [activeTab, setActiveTab] = useState('social'); // التكافل هو القسم الرئيسي
  const [showAccountModal, setShowAccountModal] = useState(false);
  const [appData, setAppData] = useState({
    accountNumber: "52067764",
    accountName: "العباس إدريس علي إدريس",
    targetAmount: 5000000,
    currentAmount: 0,
    announcement: "مرحباً بكم في تطبيق لتي قسم 2 شرق"
  });
  const [suggestions, setSuggestions] = useState([]);
  const [newSuggestion, setNewSuggestion] = useState("");
  const [isAdmin, setIsAdmin] = useState(false);
  const [adminKey, setAdminKey] = useState("");

  // الدخول التلقائي
  useEffect(() => {
    const initAuth = async () => {
      if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
        await signInWithCustomToken(auth, __initial_auth_token);
      } else {
        await signInAnonymously(auth);
      }
    };
    initAuth();
    onAuthStateChanged(auth, setUser);
  }, []);

  // جلب البيانات الحية
  useEffect(() => {
    if (!user) return;
    const settingsRef = doc(db, 'artifacts', appId, 'public', 'settings');
    const unsubSettings = onSnapshot(settingsRef, (snap) => {
      if (snap.exists()) setAppData(snap.data());
      else setDoc(settingsRef, appData);
    });

    const suggestionsRef = collection(db, 'artifacts', appId, 'public', 'suggestions');
    const unsubSuggestions = onSnapshot(suggestionsRef, (snap) => {
      const docs = snap.docs.map(d => ({ id: d.id, ...d.data() }));
      setSuggestions(docs.sort((a, b) => b.timestamp - a.timestamp));
    });

    return () => { unsubSettings(); unsubSuggestions(); };
  }, [user]);

  const handleSuggestion = async () => {
    if (!newSuggestion.trim()) return;
    await addDoc(collection(db, 'artifacts', appId, 'public', 'suggestions'), {
      text: newSuggestion,
      timestamp: Date.now()
    });
    setNewSuggestion("");
    alert("شكراً لك، تم نشر رأيك بنجاح");
  };

  const handleAdminAuth = () => {
    if (adminKey === "2510") setIsAdmin(true);
    else alert("الرمز السري غير صحيح");
  };

  const updateAppData = async () => {
    await setDoc(doc(db, 'artifacts', appId, 'public', 'settings'), appData);
    alert("تم تحديث البيانات للجميع");
    setIsAdmin(false);
  };

  return (
    <div className="min-h-screen bg-slate-50 text-right font-sans pb-28" dir="rtl">
      
      {/* الهيدر العلوي */}
      <header className="bg-gradient-to-b from-green-800 to-green-900 text-white p-6 pt-10 rounded-b-[3rem] shadow-xl relative">
        <div className="flex justify-between items-center">
          <div>
            <h1 className="text-2xl font-bold">لتي قسم 2 شرق</h1>
            <p className="text-xs opacity-75 mt-1">الولاية الشمالية - محلية القولد</p>
          </div>
          {/* أيقونة الحساب البنكي الجانبية */}
          <button 
            onClick={() => setShowAccountModal(true)}
            className="w-12 h-12 bg-amber-500 rounded-2xl flex items-center justify-center shadow-lg border-2 border-amber-400 animate-pulse"
          >
            <i className="fas fa-university text-xl"></i>
          </button>
        </div>
      </header>

      <main className="px-5 mt-6">
        
        {/* قسم التكافل - الرئيسي */}
        {activeTab === 'social' && (
          <div className="space-y-6">
            <div className="bg-white p-6 rounded-[2rem] shadow-sm border-r-4 border-green-600">
              <h3 className="font-bold text-lg mb-2 text-green-800">روح التكافل والترابط</h3>
              <p className="text-sm text-gray-600 leading-relaxed">
                هذا التطبيق يهدف لتقوية الروابط بين أهل المنطقة ومساعدة الأسر المتعففة والحالات العاجلة. 
                أبناء لتي دائماً يد واحدة.
              </p>
            </div>

            <div className="grid grid-cols-1 gap-4">
              <div className="bg-red-50 p-5 rounded-3xl border border-red-100">
                <h4 className="font-bold text-red-700 flex items-center gap-2">
                  <i className="fas fa-heartbeat"></i> الحالات العاجلة
                </h4>
                <p className="text-xs mt-2 text-red-600 opacity-80 italic">في حال وجود حالة طارئة، سيتم نشرها هنا مباشرة عبر الإدارة.</p>
              </div>
              <div className="bg-emerald-50 p-5 rounded-3xl border border-emerald-100">
                <h4 className="font-bold text-emerald-800 flex items-center gap-2">
                  <i className="fas fa-box-open"></i> دعم الأسر المتعففة
                </h4>
                <p className="text-xs mt-2 text-emerald-700">برامج السلة الغذائية والدعم الشهري مستمرة بسواعدكم.</p>
              </div>
            </div>

            <div className="bg-white p-6 rounded-[2rem] shadow-sm">
              <h4 className="font-bold mb-3 text-sm">موقف صندوق الدعم المالي:</h4>
              <div className="h-4 w-full bg-gray-100 rounded-full overflow-hidden mb-2">
                <div 
                  className="h-full bg-green-600 transition-all duration-1000"
                  style={{ width: `${Math.min(100, (appData.currentAmount / appData.targetAmount) * 100)}%` }}
                ></div>
              </div>
              <div className="flex justify-between text-[10px] font-bold">
                <span>تم جمع: {appData.currentAmount.toLocaleString()} جنيه</span>
                <span>المستهدف: {appData.targetAmount.toLocaleString()} جنيه</span>
              </div>
            </div>
          </div>
        )}

        {/* قسم الخدمات */}
        {activeTab === 'services' && (
          <div className="space-y-4">
            <h2 className="text-xl font-bold mb-4">خدمات المنطقة</h2>
            <div className="bg-white p-5 rounded-3xl shadow-sm flex items-center gap-4">
              <div className="w-12 h-12 bg-blue-100 text-blue-700 rounded-full flex items-center justify-center">
                <i className="fas fa-bolt"></i>
              </div>
              <div>
                <h4 className="font-bold text-sm">الكهرباء العامة</h4>
                <p className="text-xs text-gray-500">صيانة المحولات وإنارة الشوارع العامة.</p>
              </div>
            </div>
            <div className="bg-white p-5 rounded-3xl shadow-sm flex items-center gap-4">
              <div className="w-12 h-12 bg-amber-100 text-amber-700 rounded-full flex items-center justify-center">
                <i className="fas fa-road"></i>
              </div>
              <div>
                <h4 className="font-bold text-sm">ترميم الشوارع</h4>
                <p className="text-xs text-gray-500">ردم الطرق وتسهيل حركة المرور الداخلية.</p>
              </div>
            </div>
          </div>
        )}

        {/* قسم ركن الشباب */}
        {activeTab === 'youth' && (
          <div className="space-y-6">
            <div className="bg-white p-6 rounded-[2rem] shadow-sm">
              <h3 className="font-bold mb-4">اطرح رأيك للعمل القادم</h3>
              <textarea 
                value={newSuggestion}
                onChange={(e) => setNewSuggestion(e.target.value)}
                className="w-full bg-slate-50 p-4 rounded-2xl border-none focus:ring-2 focus:ring-green-600 outline-none text-sm"
                placeholder="اكتب هنا ما تقترحه..."
                rows="4"
              ></textarea>
              <button 
                onClick={handleSuggestion}
                className="w-full mt-3 bg-green-800 text-white py-4 rounded-2xl font-bold shadow-lg shadow-green-900/20"
              >
                نشر للجميع
              </button>
            </div>
            
            <div className="space-y-3">
              <h4 className="font-bold text-gray-400 text-xs px-2 uppercase tracking-widest">آخر المقترحات</h4>
              {suggestions.map(s => (
                <div key={s.id} className="bg-white p-4 rounded-2xl shadow-sm border-r-4 border-green-500">
                  <p className="text-sm text-gray-700">{s.text}</p>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* لوحة الإدارة */}
        {activeTab === 'admin' && (
          <div className="max-w-md mx-auto">
            {!isAdmin ? (
              <div className="bg-white p-8 rounded-[2.5rem] shadow-xl text-center">
                <i className="fas fa-lock text-4xl text-gray-200 mb-4"></i>
                <h3 className="font-bold mb-6">الدخول للمسؤول (العباس)</h3>
                <input 
                  type="password"
                  placeholder="أدخل الرمز السري"
                  className="w-full p-4 bg-slate-100 rounded-2xl mb-4 text-center"
                  onChange={(e) => setAdminKey(e.target.value)}
                />
                <button onClick={handleAdminAuth} className="w-full bg-slate-900 text-white py-4 rounded-2xl font-bold">دخول</button>
              </div>
            ) : (
              <div className="bg-white p-6 rounded-[2.5rem] shadow-xl space-y-4">
                <h3 className="font-bold text-center border-b pb-4">تحديث بيانات لتي</h3>
                <div>
                  <label className="text-[10px] font-bold text-gray-400 mr-2">رقم الحساب</label>
                  <input className="w-full p-3 bg-slate-50 rounded-xl mt-1 border" value={appData.accountNumber} onChange={e => setAppData({...appData, accountNumber: e.target.value})} />
                </div>
                <div>
                  <label className="text-[10px] font-bold text-gray-400 mr-2">المبلغ المجمع حالياً</label>
                  <input type="number" className="w-full p-3 bg-slate-50 rounded-xl mt-1 border" value={appData.currentAmount} onChange={e => setAppData({...appData, currentAmount: Number(e.target.value)})} />
                </div>
                <div>
                  <label className="text-[10px] font-bold text-gray-400 mr-2">المبلغ المستهدف</label>
                  <input type="number" className="w-full p-3 bg-slate-50 rounded-xl mt-1 border" value={appData.targetAmount} onChange={e => setAppData({...appData, targetAmount: Number(e.target.value)})} />
                </div>
                <button onClick={updateAppData} className="w-full bg-green-700 text-white py-4 rounded-2xl font-bold mt-4">حفظ وتحديث عند الجميع</button>
              </div>
            )}
          </div>
        )}

      </main>

      {/* مودال رقم الحساب (يظهر عند الضغط على الأيقونة) */}
      {showAccountModal && (
        <div className="fixed inset-0 bg-black/60 backdrop-blur-sm z-[2000] flex items-center justify-center p-6">
          <div className="bg-white w-full max-w-sm rounded-[3rem] p-8 text-center animate-in zoom-in duration-300">
            <div className="w-20 h-20 bg-amber-100 text-amber-600 rounded-full flex items-center justify-center mx-auto mb-4">
              <i className="fas fa-university text-3xl"></i>
            </div>
            <h3 className="text-xl font-bold text-gray-800 mb-2">بيانات التحويل</h3>
            <p className="text-xs text-gray-500 mb-6">بنك فيصل الإسلامي السوداني</p>
            
            <div className="bg-slate-50 p-4 rounded-3xl border-2 border-dashed border-slate-200 mb-6">
              <p className="text-2xl font-mono font-bold tracking-widest text-slate-800 mb-2">{appData.accountNumber}</p>
              <p className="text-sm font-bold text-slate-600">{appData.accountName}</p>
            </div>

            <button 
              onClick={() => {
                navigator.clipboard.writeText(appData.accountNumber);
                alert("تم نسخ رقم الحساب");
              }}
              className="w-full bg-amber-500 text-white py-4 rounded-2xl font-bold mb-3 shadow-lg shadow-amber-500/30"
            >
              نسخ رقم الحساب
            </button>
            <button onClick={() => setShowAccountModal(false)} className="text-gray-400 font-bold text-sm">إغلاق</button>
          </div>
        </div>
      )}

      {/* الملاحة السفلية */}
      <nav className="fixed bottom-0 left-0 right-0 bg-white/80 backdrop-blur-md border-t h-24 px-4 flex justify-around items-center z-[1000]">
        <button onClick={() => setActiveTab('social')} className={`flex flex-col items-center gap-1 ${activeTab === 'social' ? 'text-green-700' : 'text-slate-400'}`}>
          <i className="fas fa-hand-holding-heart text-xl"></i>
          <span className="text-[10px] font-bold">التكافل</span>
        </button>
        <button onClick={() => setActiveTab('services')} className={`flex flex-col items-center gap-1 ${activeTab === 'services' ? 'text-green-700' : 'text-slate-400'}`}>
          <i className="fas fa-tools text-xl"></i>
          <span className="text-[10px] font-bold">الخدمات</span>
        </button>
        <button onClick={() => setActiveTab('youth')} className={`flex flex-col items-center gap-1 ${activeTab === 'youth' ? 'text-green-700' : 'text-slate-400'}`}>
          <i className="fas fa-users text-xl"></i>
          <span className="text-[10px] font-bold">الشباب</span>
        </button>
        <button onClick={() => setActiveTab('admin')} className={`flex flex-col items-center gap-1 ${activeTab === 'admin' ? 'text-green-700' : 'text-slate-400'}`}>
          <i className="fas fa-user-shield text-xl"></i>
          <span className="text-[10px] font-bold">الإدارة</span>
        </button>
      </nav>

    </div>
  );
}

