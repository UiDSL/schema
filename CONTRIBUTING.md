# 🤝 Contributing to UiDSL Spec

Thank you for considering contributing to **UiDSL**! We're building a declarative UI spec standard tightly coupled to TailwindCSS for rapidly generating maintainable, API-driven UI for both web and native.

---

## 🧱 Ways You Can Contribute

### 1. 💻 Code Contributions

- Add improvements to the UiDSL JSON Schema
- Create or enhance JSX code generators (React Web / Native)
- Build CLI tools for validation or generation
- Help integrate UiDSL with OpenAPI (auto-mapping, validation, etc.)

### 2. 🧩 Component Templates

We’re planning to support reusable UI component templates for common libraries like:

- ShadCN
- Gluestack UI
- Chakra UI

You can help by contributing:

- Template definitions in the `components/` section
- JSON examples for screen usage
- Styling conventions and layout presets

### 3. 🧪 Examples

Submit example UiDSL specs for:

- Login screen
- Dashboard
- CRUD list + detail views
- Mobile-first layouts

Place these under the `/examples` folder.

### 4. 🧰 Tooling

- Build GUI editors for UiDSL (e.g. drag-n-drop editors, Figma plugins)
- Improve validator UX
- Add support for other formats (YAML, DSL)

---

## ✅ Getting Started

1. Fork the repo
2. Clone it locally:  
   ```bash
   git clone https://github.com/YOUR_USERNAME/uidsl.git
   ```
3. Install dependencies for any tooling (if applicable)
4. Create a new branch:
   ```bash
   git checkout -b feature/my-contribution
   ```

---

## 📦 Folder Structure

```
.
├── uidsl.tailwind.schema.json   # JSON Schema definition
├── examples/                     # UI spec examples
├── generators/                   # JSX/Tailwind generator logic
├── templates/                    # Planned reusable component templates
├── docs/                         # Spec and usage documentation
├── README.md
└── CONTRIBUTING.md
```

---

## 🧪 Validation

Before submitting changes to schema or templates:

```bash
npm install -g ajv-cli

ajv validate -s uidsl.tailwind.schema.json -d examples/login.json
```

---

## 📝 Pull Request Guidelines

- Explain **why** you’re proposing the change.
- Keep PRs **focused and atomic** — one feature per PR.
- Include sample usage or test files if applicable.
- If modifying the schema, update the examples and documentation accordingly.

---

## 🗣️ Communication

Feel free to open an issue for:
- Feature requests
- Bug reports
- Questions about contributing

---

## 📜 License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

Thanks for helping improve the UiDSL ecosystem!
