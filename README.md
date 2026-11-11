# Revive Education — Vercel + Firebase সেটআপ

## ১. Firebase প্রজেক্ট (বিনামূল্যে)
1. https://console.firebase.google.com → **Add project**
2. **Build → Authentication → Get started → Email/Password → Enable**
3. **Build → Firestore Database → Create database** (production mode)
4. Firestore → **Rules** ট্যাবে `firestore.rules` ফাইলের লেখা পুরো paste করে **Publish**
5. Project settings (⚙) → **Your apps → Web (</>)** → app register করো → যে `firebaseConfig` দেখাবে সেটা কপি করো
6. `index.html`-এ `const cfg={...}` লাইনে `apiKey`, `authDomain`, `projectId`, `appId` বসাও

## ২. Admin account
1. Authentication → **Users → Add user**: Email `admin@revive-education.com`, Password দাও
2. ওই user-এর **User UID** কপি করো
3. Firestore → **Start collection** → ID: `admins` → Document ID = সেই UID → field `ok` (boolean) = `true`
4. সাইটে Login-এ Email ঘরে `Nayem1797#` লিখে Password দিলেই Admin হিসেবে ঢুকবে (অন্য কেউ admin হতে পারবে না, নিয়ম Firestore-এ বাঁধা)

⚠ Password পাবলিকলি শেয়ার করেছ, তাই Firebase-এ শক্ত নতুন password দাও।

## ৩. Vercel-এ হোস্ট
1. `index.html` ফাইলটি একটা GitHub repo-তে রাখো (বা Vercel CLI: `vercel`)
2. https://vercel.com → **Add New → Project** → repo import → Deploy (কোনো build সেটিং লাগবে না)
3. Deploy হলে যে ডোমেইন (`xxx.vercel.app`) পাবে, সেটা Firebase → Authentication → **Settings → Authorized domains**-এ যোগ করো

## ৪. ব্যবহার
Admin Login → **Payment Setup** (bKash/Nagad নম্বর) → **Courses** (course/resource, প্রতি lesson-এর আলাদা টাইটেল + YouTube লিংক)।
Student Sign Up → Buy → Request → Admin **Accept** → My Learning-এ ভিডিও সাইটের ভেতরেই চলবে।
