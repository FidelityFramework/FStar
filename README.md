F*: A Proof-oriented Programming Language
=========================================

## Fidelity Framework Fork

This is a fork of [FStarLang/FStar](https://github.com/FStarLang/FStar) maintained by the [Fidelity Framework](https://github.com/FidelityFramework) project. The fork adds support for extracting verified F* code to native F# via [fsnative](https://github.com/FidelityFramework/fsnative) (F# Native Compiler Services).

### Why This Fork Exists

F* can extract verified code to OCaml, F#, C (via KaRaMeL), and WebAssembly. The standard F# extraction targets .NET and the Base Class Library. This fork adds a new extraction target: native F# that compiles through [Firefly](https://github.com/FidelityFramework/Firefly) to standalone binaries without a .NET runtime.

The integration enables formal verification with proofs that persist through compilation. F* generates proofs; the Fidelity pipeline preserves them through MLIR code generation, where they guide optimization and validate transformations. For architectural details, see the [FStar Integration](https://github.com/FidelityFramework/Firefly/blob/main/docs/FStar_Integration.md) document in Firefly.

### Fork Structure

Development occurs on the `fidelity` branch. The `main` branch tracks upstream FStarLang/FStar. General improvements are cherry-picked to `main` and submitted as pull requests upstream.

The fork adds:
- `fsnative/` - Runtime library targeting native F# (peer to `fsharp/`)
- Extraction backend modifications for fsnative-compatible output

### Current Status

This integration is in early development. The fsnative extraction target is not yet functional. If you're looking to use F* today, we recommend the upstream [FStarLang/FStar](https://github.com/FStarLang/FStar) repository with its well-maintained OCaml extraction.

---

## About F*

F* is a proof-oriented programming language developed at Microsoft Research and INRIA. It enables writing programs together with their specifications and proofs, with the proofs checked automatically by an SMT solver. F* code can be extracted to OCaml, F#, C, or WebAssembly for execution.

If you're an F# developer curious about formal verification, F* is an excellent entry point. The language shares ML heritage with F#, and the syntax will feel familiar. The [online book](#online-book) provides a gentle introduction.

### F\* website

More information on F\* can be found at www.fstar-lang.org

### Installation

See [INSTALL.md](https://github.com/FStarLang/FStar/blob/master/INSTALL.md)

### Online book

An online book _Proof-oriented Programming In F*_ is in the works and regular updates are
posted online. The book is available as a [PDF], or you can read it while trying out
examples and exercises in your browser interface from this [tutorial page].

[tutorial page]: https://www.fstar-lang.org/tutorial/
[PDF]: http://fstar-lang.org/tutorial/proof-oriented-programming-in-fstar.pdf

### Wiki

The [F\* wiki] contains additional technical documentation on F\*, and is especially useful
for topics that are not yet covered by the book.

[F\* wiki]: https://github.com/FStarLang/FStar/wiki

### Editing F* code

You can edit F\* code using various text editor. Emacs has the best support currently,
providing syntax highlighting, code completion and navigation, and interactive development,
using [fstar-mode.el]. However, other editors also have limited support.
More details on [editor support] are available on the [F\* wiki].

[editor support]: https://github.com/FStarLang/FStar/wiki/Editor-support-for-F*
[fstar-mode.el]: https://github.com/FStarLang/fstar-mode.el

### Extracting and executing F* code

By default F* only verifies the input code, it does not compile or execute it.
To execute F* code one needs to translate it for instance to OCaml or F\#,
using F\*'s code extraction facility---this is invoked using the
command line argument `--codegen OCaml` or `--codegen FSharp`.
More details on [executing F\* code via OCaml] on the [F\* wiki].

[executing F\* code via OCaml]: https://github.com/FStarLang/FStar/wiki/Executing-F*-code

Also, code written in a C-like shallowly embedded DSL can be extracted to
[C](https://arxiv.org/abs/1703.00053)
or [WASM](https://doi.ieeecomputersociety.org/10.1109/SP.2019.00064)
by the [KaRaMeL tool](https://github.com/FStarLang/karamel),
and code written in an ASM-like deeply embedded DSL can be extracted
to ASM by the [Vale tool](https://github.com/project-everest/vale).

### Chatting about F* on Slack and Zulip

The F* developers and many users interact on this [Slack
forum](https://everestexpedition.slack.com)---you should be able to
join automatically by [clicking
here](https://aka.ms/JoinEverestSlack),
but if that doesn't work, please contact the mailing list mentioned
below.

Users can also chat about F* or ask questions at this [Zulip
forum](https://fstar.zulipchat.com).

### Mailing list

We also have a [mailing list] which we use mainly for announcements.

[mailing list]: https://groups.google.com/g/fstar-mailing-list

### Reporting issues

For issues specific to the Fidelity fork (fsnative extraction, native compilation), please use the [Fidelity FStar issue tracker](https://github.com/FidelityFramework/FStar/issues).

For general F* issues, please use the upstream [F\* issue tracker] on GitHub.
Before filing please search to make sure the issue doesn't already exist.
We don't maintain old releases, so if possible please use the
[online F\* editor] or directly [the GitHub sources] to check
that your problem still exists on the `master` branch.

[F\* issue tracker]: https://github.com/FStarLang/FStar/issues
[online F\* editor]: https://www.fstar-lang.org/run.php
[the GitHub sources]: https://github.com/FStarLang/FStar/blob/master/INSTALL.md#building-f-from-sources

### Contributing

For contributions to fsnative extraction, see the Fidelity Framework [contributing guidelines](https://github.com/FidelityFramework/.github/blob/main/profile/README.md#contributing).

For general F* contributions, see [CONTRIBUTING.md](https://github.com/FStarLang/FStar/blob/master/CONTRIBUTING.md)

### License

F* is released under the [Apache 2.0 license]; for more details
see [LICENSE](https://github.com/FStarLang/FStar/blob/master/LICENSE)

[Apache 2.0 license]: https://www.apache.org/licenses/LICENSE-2.0

### Related Projects

- [HACL*](https://github.com/hacl-star/hacl-star): Verified cryptographic library built with F*
- [Project Everest](https://project-everest.github.io/): Verified secure communication stack
- [KaRaMeL](https://github.com/FStarLang/karamel): F* to C extraction
- [Vale](https://github.com/project-everest/vale): Verified assembly code
