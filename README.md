# Setup express serverless 

Panduan untuk mendeploy project express + hbs ke vercel sebagai serverless, panduan ini perlu penyesuaian tidak bisa copy paste semua

## 1. Buat folder api/index.js di root project
```js
// sesuaikan dengan lokasi index.js atau app.js
import  app  from  "../src/app.js";
export  default  app;
```

## 2. Pastikan di index.js atau app.js itu 
```js
  const  app  =  express();
  // code kamu lainya
  
  // pastikan export
  export  default  app;

// ini di comment
// app.listen(PORT, () => {
// console.log(`🚀 Server running on http://localhost:${PORT}`);
// });
```
## 3. Buat file vercel.json di root project
```json
{
	"version": 2,
	"builds": [
		{
			"src": "api/index.js",
			"use": "@vercel/node"
		}
	],

	"routes": [
		{
			"src": "/(.*)",
			"dest": "/api/index.js"
		}
	]
}
```

## 4 Tambah atau ubah script di package.json
```js
"scripts": {
	"dev": "vercel dev",
	"start": "node api/index.js"
},
```

## 5. Selesai
- Tinggal push ke github dan import di vercel

## Catatan
- kalo ingin jalankan di local, kamu harus menginstall vercel di local tanya ai saja caranya bagaimana
