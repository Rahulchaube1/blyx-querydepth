<img src="assets/logo.png" width="112" height="112" alt="Blyx penguin lowering a plumb line through a tree of query fields.">

# QueryDepth

Validate a preorder field-depth trace from an expanded query plan. This Blyx library is part of the graphql, rpc and http collection.

A flat query can cost more than a deep one when list fields fan out. Evaluate expanded cost and depth independently. [GraphQL, demand control](https://graphql.org/learn/security/)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-querydepth.git
cd blyx-querydepth
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-querydepth) · [Package page](https://www.blyx-lang.space/packages/querydepth) · [Handbook](https://doc.blyx-lang.space/guide/waxwing)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-querydepth.git vendor/querydepth
```

```blyx
use vendor::querydepth::querydepth;

fn main() {
    let depths = [1, 2, 3, 2, 1];
    let result = querydepth_shape(depths);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
3
2
5
```

## API

`querydepth_shape(depths)`

Returns [maximum depth, root fields, total fields]. Depth starts at one. A child can descend only one level; siblings and ascent are allowed. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| depths | Vector of values, each a nonnegative exact integer |

## In use

[Waxwing](https://github.com/Rahulchaube1/blyx-waxwing) uses this module to check the depth and weighted resolver cost of an expanded GraphQL field plan.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-querydepth/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). Read the [artwork notice](assets/NOTICE.txt) for credits.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
