
![minified size](https://badgen.net/bundlephobia/min/@hoangcung1804npm/id-dolore-itaque) ![minified zipped size](https://badgen.net/bundlephobia/minzip/@hoangcung1804npm/id-dolore-itaque) ![types](https://badgen.net/npm/types/@hoangcung1804npm/id-dolore-itaque) ![license](https://badgen.net/npm/license/@hoangcung1804npm/id-dolore-itaque) [![npm-publish](https://github.com/hoangcung1804npm/id-dolore-itaque/actions/workflows/npm-publish.yml/badge.svg)](https://github.com/hoangcung1804npm/id-dolore-itaque/actions/workflows/npm-publish.yml)

# Social Links

Social Links is helping to detect, validate and sanitize social (desktop & mobile) links

### Install
```bash
npm i @hoangcung1804npm/id-dolore-itaque --save
```

### Demo

- https://awesome-web-tools.web.app/@hoangcung1804npm/id-dolore-itaque - Example use case
- https://gkucmierz.github.io/@hoangcung1804npm/id-dolore-itaque-app - Detect profile demo (v1.7.0)

### Using
```js
import { SocialLinks, TYPE_MOBILE } from '@hoangcung1804npm/id-dolore-itaque';
const socialLinks = new SocialLinks();

const link = 'http://www.linkedin.com/in/gkucmierz';
const profileName = socialLinks.detectProfile(link); // 'linkedin'

console.log(socialLinks.isValid(profileName, link)); // true
console.log(socialLinks.sanitize(profileName, link)); // 'https://linkedin.com/in/gkucmierz'
console.log(socialLinks.sanitize(profileName, link, TYPE_MOBILE)); // 'https://linkedin.com/mwlite/in/gkucmierz'
```

Above examples works based on predefined **linkedin** profile:
```js
import { Profile } from '@hoangcung1804npm/id-dolore-itaque';
const linkedinProfile: Profile =
{ name: 'linkedin',
    matches: [
      {
        match: '(https?://)?(www.)?linkedin.com/in/({PROFILE_ID})', group: 3, type: TYPE_DESKTOP,
        pattern: 'https://linkedin.com/in/{PROFILE_ID}'
      },
      {
        match: '(https?://)?(www.)?linkedin.com/mwlite/in/({PROFILE_ID})', group: 3, type: TYPE_MOBILE,
        pattern: 'https://linkedin.com/mwlite/in/{PROFILE_ID}'
      },
      { match: '({PROFILE_ID})', group: 1 },
    ]
};
```

### Add new profile
```js
import { SocialLinks, Profile } from '@hoangcung1804npm/id-dolore-itaque';

const socialLinks = new SocialLinks();
const profileMatches: ProfileMatch[] = [ ... ];

socialLinks.addProfile('profileName', profileMatches);
```

### Configuration
```js
import { SocialLinks, Config } from '@hoangcung1804npm/id-dolore-itaque';

const config: Config = {
  usePredefinedProfiles: true,
  trimInput: true,
  allowQueryParams: false,
};
const socialLinks = new SocialLinks(config);
```

### Build

Watch, *tsc* build
```bash
npm run start
```

### Tests

Just *jest* tests
```bash
npm run test
```
or
```bash
npm run test:watch
```

### Contributing

[CONTRIBUTING.md](CONTRIBUTING.md)
