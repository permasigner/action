# Permasigner Action

<p align="center">
  <img src="https://static.itsnebula.net/permasigner-title.png" width="240" />
</p>

<p align="center">
  <a href="#">
    <img src="https://img.shields.io/badge/made%20with-love-E760A4.svg" alt="Made with love">
  </a>
  <a href="https://github.com/permasigner/action/blob/main/LICENSE" target="_blank">
    <img src="https://img.shields.io/github/license/permasigner/action.svg" alt="License">
  </a>
  <a href="https://dsc.gg/permasigner" target="_blank">
    <img src="https://img.shields.io/discord/1001905994458206229?label=discord" alt="Discord">
  </a>
  <a href="https://github.com/permasigner/action/actions" target="_blank">
    <img src="https://img.shields.io/github/workflow/status/permasigner/action/Test%20action/main.svg" alt="Test status">
  </a>
</p>

<p align="center">
GitHub action for Permasigner, useful for CI/CD.
</p>

---

# Why is this useful?

If you're an iOS developer, and your app has a jailbroken and jailed version, you may want to create a permasigned version of the jailbroken one with necessary entitlements to run correctly jailed (as if the device was in a jailbroken state).

For example, [Santander](https://github.com/SerenaKit/Santander) has an IPA along as a permasigned deb. The IPA will work both jailed and jailbroken, but will be limited to a sandboxed directory when not in a jailbroken state. The deb on the other hand, will work the same jaied and jailbroken, and will not be constrained to a sandboxed directory when jailed.

# How do I use it?

First of all, make sure you're using a Linux or macOS runner, Windows will not work! Then, you'll want to add it to your CI/CD workflow like this:

```yaml
- name: Run Permasigner
  uses: permasigner/action@v1
  with:
    # Specify your IPA as an input
    input: "${GITHUB_WORKSPACE}/MyApp.ipa"

    # Optional: Run the latest version of Permasigner instead of the PyPi package
    # source: true

    # Optional: Set the output directory (default is ${GITHUB_WORKSPACE}/permasigner-out)
    # output: "${GITHUB_WORKSPACE}/a-cooler-output"

    # Optional: Specify your custom entitlements
    # entitlements: "${GITHUB_WORKSPACE}/entitlements.plist"

    # Optional: Pass more args to Permasigner
    # args: "--ldidfork ProcursusTeam --author Nebula --name 'My Cool App'"
```

An example workflow is [here](https://github.com/permasigner/action/blob/main/.github/workflows/test.yml), we use it to test the action and make sure it works correctly for users.

# Can I contribute?

Of course, make a fork, make your changes, and make a pull request as usual!

# Credits

- [Beerpsi](https://github.com/beerpiss) for the Install Procursus action

# License

The Permasigner action is licensed under the BSD-3-Clause license, and can be found [here](https://github.com/permasigner/action/blob/main/LICENSE).
