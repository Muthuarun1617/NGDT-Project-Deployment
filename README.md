# 🌐 DevNGDTWebApp - Frontend Deployment with GitHub Actions & Azure

![deploy](https://github.com/user-attachments/assets/77c46148-3279-4816-ada3-a6b9d1ee50c2)


Automated CI/CD pipeline for a **Vite-powered frontend application** using **GitHub Actions** and deployment to **Azure Web App**. This setup ensures efficient build, artifact management, logging, and automated deployment on every push to the `dev` branch.

---

## 🚀 Workflow: `deploy.yml`

### 🔄 Trigger

- On every push to the `dev` branch.

---

## 🛠️ Job Breakdown

### 📦 Build Job

Runs on **Ubuntu** and performs the following:

1. **Checkout Code**  
   Fetches the latest code from the repository.

2. **Set up Node.js**  
   Uses Node.js version 18.

3. **Install Dependencies**  
   Runs `npm install`.

4. **Build Vite App**  
   Builds the app with `npm run build` and checks for the `dist` folder.

5. **Debug Listing**  
   Lists contents of the `dist/` folder.

6. **Upload Artifacts**  
   - Uploads the `dist/` folder as `build-artifacts`
   - Uploads `build.log` as `build-logs`

---

### 🚚 Deploy Job

Depends on `build` job completion and includes:

1. **Checkout Code**  
   Ensures fresh context.

2. **Download Artifacts**  
   Pulls `build-artifacts` and `build-logs`.

3. **Show Logs**  
   Outputs build logs for visibility.

4. **Install PM2**  
   Sets up PM2 to serve static files.

5. **Serve App with PM2**  
   Serves `./dist` folder as SPA using PM2.

6. **Deploy to Azure**  
   Deploys the built app to Azure Web App `DevNGDTWebApp` using GitHub secret `AZURE_PUBLISH_PROFILE`.

---

## 🖼 Screenshots

### ✔️ Vite Build Success

![Features-of-Vite-JS-2 0](https://github.com/user-attachments/assets/471472b7-2feb-4887-afb8-0869c6967132)

### ☁️ Azure Web Deployment

![azure web development](https://github.com/user-attachments/assets/0bc97c17-e190-44b2-9a96-b142a2c3da71)


---

## 📋 Prerequisites

- Azure Web App created and configured
- GitHub secret:
  - `AZURE_PUBLISH_PROFILE` (from Azure portal)
- Node.js 18 configured in GitHub Actions
- Vite configured correctly (`vite.config.js`)

---

## 💡 Best Practices

- Add branch protection to `dev` for PR-based changes.
- Use status checks to prevent merge until CI passes.
- Store build logs to help debug deployment failures.
- Use PM2 for simple SPA serving — for production, consider Azure Static Web Apps or CDN fronting.

---

## 👥 Contributing

1. Fork the repo
2. Create a feature branch (`feature/your-feature`)
3. Push and open a PR to `dev`
4. CI/CD will handle the rest!

---

## 📜 License

Licensed under the [MIT License](LICENSE).

---

## 📫 Support

Open an issue or reach out if you encounter problems or have suggestions!

---

## CONTACT:

[![LinkedIn](https://img.shields.io/badge/-LinkedIn-blue?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/muthuarun/)
[![GitHub](https://img.shields.io/badge/-GitHub-black?style=flat-square&logo=github)](https://github.com/Muthuarun1617)

---
