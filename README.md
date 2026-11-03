# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some Oxlint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Oxc](https://oxc.rs)
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/)

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the Oxlint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and Oxlint's TypeScript related rules in your project.


## FinGuard backend connection

Create `.env.local` in this frontend folder with:

```
VITE_FINGUARD_API_URL=http://127.0.0.1:8000
```

Start the backend first, then run `npm run dev`. Importing a CSV sends the normalized
transaction records to `POST /api/v1/transactions/scan`; the security report now renders
the backend response. The scan uses a synthetic demo ML model plus review rules; its
scores are not validated fraud probabilities and it does not block payments. Do not put backend secrets in Vite environment
variables because browser code is public.


### Scan alerts

A completed backend scan displays an in-app priority alert. Low risk is silent, a medium review alert plays one short beep, and high risk plays five short beeps. Audio is primed only when the user starts a scan, as required by browser audio policies. Desktop notifications are optional and require the user to enable them in the report. Alerts summarize the synthetic demo screening output and are not confirmed fraud determinations.
