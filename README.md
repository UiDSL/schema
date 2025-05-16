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

## 🧠 Why UiDSL Instead of HTML?

UiDSL is **not** just a verbose version of HTML — it is a **platform-agnostic UI abstraction layer** designed for:

- Cross-platform generation (React, React Native, Flutter, etc.)
- Declarative bindings to data, state, and events
- Reusable components and schema-driven definitions
- Generator-based output using tailored primitives like `container`, `text`, `input`, etc.

### Example Translation of `container`
| Platform      | Output           |
|---------------|------------------|
| Web (React)   | `<div>`          |
| React Native  | `<View>`         |
| Flutter       | `Container()`    |

This makes it ideal for design systems, prototyping tools, or AI agents that need to define UI once and target multiple runtimes.

### 🔍 How Are Primitives Decided?
UiDSL includes a small set of **core primitives** that are:
- Universally supported across platforms (e.g., web, native, mobile)
- Atomic in nature (cannot be decomposed further within the schema)
- Interpretable directly by all generators

Examples include: `text`, `input`, `button`, `switch`, etc.

More complex or composed elements (like `card`, `form`, `modal`, `tabs`) should be defined as **custom components** instead.

📬 **Want to propose a new primitive?** Open a [discussion](https://github.com/your-repo/discussions) and share your use case. We're open to feedback!

### ✅ Supported Primitives and Platform Mappings
| Primitive   | Web (React) | React Native      |
|-------------|-------------|-------------------|
| `container` | `<div>`     | `<View>`          |
| `text`      | `<span>`    | `<Text>`          |
| `image`     | `<img>`     | `<Image>`         |
| `input`     | `<input>`   | `<TextInput>`     |
| `button`    | `<button>`  | `<TouchableOpacity>` or `<Button>` |
| `label`     | `<label>`   | `<Text>`          |
| `icon`      | `<svg>` / `<i>` | icon component from lib |
| `checkbox`  | `<input type="checkbox">` | `<CheckBox>` (or custom) |
| `radio`     | `<input type="radio">`    | `<RadioButton>` (or custom) |
| `select`    | `<select>`  | `<Picker>` (or custom) |
| `switch`    | Styled checkbox or custom switch | `<Switch>`          |

📬 **Want to propose a new primitive?** Open a [discussion](https://github.com/your-repo/discussions) and share your use case. We're open to feedback!

### Notable Capabilities
| Feature                   | HTML | UiDSL |
|---------------------------|------|-------|
| Platform-agnostic         | ❌   | ✅    |
| Dynamic data binding      | ❌   | ✅    |
| Declarative events        | ❌   | ✅    |
| Component reuse (`ref`)   | ❌   | ✅    |
| Generator extensibility   | ❌   | ✅    |

## 📦 Features

- 🔧 **Screen-by-screen UI descriptions**
- 🔗 **Bind UI to OpenAPI operations**
- 🎨 **First-class TailwindCSS support**
- ⚛️ **Convert spec to JSX (React 19+)**
- 📱 **Compatible with Web & React Native + NativeWind**
- 🧠 **Declarative events, navigation, and API calls**
- 💎 **Extensible for future template support (ShadCN, Gluestack UI, etc.)**

## 📁 Repository Structure

```
.
├── uidsl.tailwind.schema.json    # JSON Schema definition (TailwindCSS only)
├── examples/                      # Example UI specs (login, dashboard, etc.)
├── docs/                          # Detailed documentation (WIP)
├── generators/                    # Code generators (JSX/Tailwind, CLI, etc.)
└── README.md                      # You are here
```

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

## 🧱 Planned: Prebuilt Component Templates

We're planning to release **optional UiDSL component templates** for popular UI libraries, so you don’t have to define low-level component structures manually:

- ✅ `tailwind-default` — default atomic components
- 🔜 `shadcn-template` — uses ShadCN UI primitives
- 🔜 `gluestack-template` — for React Native apps
- 🔜 `chakra-template` — Chakra UI-based scaffolds

Templates will include reusable component definitions that plug into `components` section of your spec.

## 🧪 Example

Checkout [`examples`](./examples/) directory.

## 📖 Documentation (*coming soon*)

- [Spec Overview](docs/spec.md)
- [Component Definitions](docs/components.md)
- [Generators](docs/generators.md)

## 💬 Join the Discussion

Have ideas? Found a limitation? Want to contribute a generator or template?

→ Open an issue or start a discussion!

## 📝 License

MIT

## 🔮 Future Plans

- [ ] CLI generator (React JSX output)
- [ ] Figma-to-UiDSL plugin
- [ ] Drag-and-drop UI builder
- [ ] OpenAPI → UiDSL auto-mapper

---

**Build UI as predictably as you build APIs. Welcome to UiDSL.**
