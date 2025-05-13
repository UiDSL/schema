# 🧩 UiDSL Spec

A declarative, extensible JSON-based schema to define screen-by-screen UI layouts directly from OpenAPI specs — tightly coupled with **TailwindCSS** for seamless, styled UI generation on **web and native** platforms.


> [!CAUTION]
>
> UiDSL is currently in **pre-alpha**. We are actively developing the specification and tools to make it mature enough for real-world prototyping. At this stage, UiDSL is **not ready for full-scale production apps**. Expect breaking changes, incomplete features, and evolving APIs as we work toward a stable release.
>
> We welcome feedback and early experimentation, but please do not use UiDSL for critical production projects yet.

## 🚀 What is UiDSL?

UiDSL is a specification format (like OpenAPI, but for UI) that enables developers to:

- Describe UI screens using structured JSON
- Map API data (from OpenAPI specs) directly to forms, tables, and views
- Generate React (web or native) components automatically using TailwindCSS
- Handle state, navigation, and events declaratively

This lets teams build interfaces that are consistent, maintainable, and tightly aligned with the backend.

---

## 📦 Features

- 🔧 **Screen-by-screen UI descriptions**
- 🔗 **Bind UI to OpenAPI operations**
- 🎨 **First-class TailwindCSS support**
- ⚛️ **Convert spec to JSX (React 19+)**
- 📱 **Compatible with Web & React Native + NativeWind**
- 🧠 **Declarative events, navigation, and API calls**
- 💎 **Extensible for future template support (ShadCN, Gluestack UI, etc.)**

---

## 📁 Repository Structure

```
.
├── uidsl.tailwind.schema.json    # JSON Schema definition (TailwindCSS only)
├── examples/                      # Example UI specs (login, dashboard, etc.)
├── docs/                          # Detailed documentation (WIP)
├── generators/                    # Code generators (JSX/Tailwind, CLI, etc.)
└── README.md                      # You are here
```

---

## 🔨 Getting Started

1. **Install a validator**

```bash
npm install -g ajv-cli
```

2. **Validate your spec**

```bash
ajv validate -s uidsl.tailwind.schema.json -d your-ui-spec.json
```

3. **Generate JSX (WIP)**

```bash
node generators/jsx-from-uidsl.js your-ui-spec.json
```

---

## 🧱 Planned: Prebuilt Component Templates

We're planning to release **optional UiDSL component templates** for popular UI libraries, so you don’t have to define low-level component structures manually:

- ✅ `tailwind-default` — default atomic components
- 🔜 `shadcn-template` — uses ShadCN UI primitives
- 🔜 `gluestack-template` — for React Native apps
- 🔜 `chakra-template` — Chakra UI-based scaffolds

Templates will include reusable component definitions that plug into `components` section of your spec.

---

## 🧪 Example

```json
{
  "uidsl": "1.0.0",
  "defaultLibrary": "TailwindCSS",
  "screens": {
    "Login": {
      "route": "/login",
      "state": {
        "formData": {
          "username": "",
          "password": ""
        }
      },
      "components": [
        {
          "type": "form",
          "children": [
            {
              "type": "input",
              "bind": "formData.username",
              "props": {
                "label": "Username",
                "className": "mb-2"
              }
            },
            {
              "type": "input",
              "bind": "formData.password",
              "props": {
                "label": "Password",
                "type": "password"
              }
            },
            {
              "type": "button",
              "props": {
                "text": "Login",
                "className": "bg-blue-500 text-white"
              },
              "events": {
                "onClick": {
                  "action": "submit",
                  "target": "loginForm"
                }
              }
            }
          ],
          "events": {
            "onSubmit": {
              "action": "apiCall",
              "api": "loginUser",
              "data": "formData",
              "onSuccess": {
                "action": "navigate",
                "target": "Dashboard"
              }
            }
          }
        }
      ]
    }
  }
}
```

---

## 📖 Documentation

- [Spec Overview](docs/spec.md)
- [Component Definitions](docs/components.md)
- [Generators](docs/generators.md) *(Coming soon)*

---

## 💬 Join the Discussion

Have ideas? Found a limitation? Want to contribute a generator or template?

→ Open an issue or start a discussion!

---

## 📝 License

MIT

---

## 🔮 Future Plans

- [ ] CLI generator (React JSX output)
- [ ] Figma-to-UiDSL plugin
- [ ] Drag-and-drop UI builder
- [ ] OpenAPI → UiDSL auto-mapper

---

**Build UI as predictably as you build APIs. Welcome to UiDSL.**
