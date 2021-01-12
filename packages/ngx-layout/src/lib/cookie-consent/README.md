# @acpaas-ui/ngx-layout

The Cookie consent module provides an easy, minimal configuration setup to add a cookie consent to your app, using Insites' [cookie consent package](https://cookieconsent.insites.com).

## Dependencies

- [cookieconsent](https://cookieconsent.insites.com)

## Usage

```typescript
import { CookieconsentModule } from '@acpaas-ui/ngx-layout';
```

## Documentation

Visit our [documentation site](https://acpaas-ui.digipolis.be/) for full how-to docs and guidelines

### Methods

| Method         | Description |
| -----------    | -------------------------- |
| `init(config: CookieConsentConfig): void` | Initiate the cookie config (when `autoInit` was set to false). |

The complete `CookieConsentConfig` API is documented on the [Insites documentation page](https://cookieconsent.insites.com/documentation/javascript-api/)/ However, to limit the visual flexibility of the component, some options are disabled. You can still provide the following custom content and cookie options.

#### `autoInit`

Boolean, default set to `true`.

#### `content`

| Name         | Default value | Description |
| -----------  | ------ | -------------------------- |
| `message: string;` | `'We make use of cookies to ensure you get the best experience on our website.'` | The main message. |
| `dismiss: string;` | `'OK'` | The dismiss button text. |
| `link: string;` | `'Learn more'` | The text accompanying the href defined above. |
| `href: string;` | `'http://cookiepedia.co.uk/all-about-cookies'` | A *read more* url. |

#### `cookie`

| Name         | Default value | Description |
| -----------  | ------ | -------------------------- |
| `name: string;` | `'cookieconsent_status'` | The key that will be used for the cookie. |
| `path: string;` | `'/'` | URL path that the cookie ‘name’ belongs to, the cookie can only be read at this location. |
| `domain: string;` | `''` | The [cookie domain](http://erik.io/blog/2014/03/04/definitive-guide-to-cookie-domains/) that the cookie **name** belongs to, the cookie can only be read on this domain. |
| `expiryDays: number;` | `365` | The amount of days after which the cookie will expire. |

#### `elements`

| Name         | Default value | Description |
| -----------  | ------ | -------------------------- |
| `messagelink: string;` | `'<p id="cookieconsent:desc">{{message}} <a aria-label="learn more about cookies" tabindex="0" href="{{href}}" target="_blank">{{link}}</a></p>'` | The html markup for the cookie consent design |
| `dismiss: string;` | `'<button aria-label="Dismiss cookie message" tabindex="0" class="a-button a-button--secondary cc-btn cc-dismiss">{{dismiss}}</button>'` | The html markup for the dismiss button. If button must have the classes `.cc-btn` and `.cc-dismiss` in order to work properly. |

### Example

```typescript
import { CookieconsentModule } from '@acpaas-ui/ngx-layout';

@NgModule({
    imports: [
        CookieconsentModule.forRoot({
            autoInit: false,
            content: {
                message: 'I am the cookie consent ngx-logo. Will you allow my cookies?',
                dismiss: 'Allow cookies',
                link: 'Learn more',
                href: 'http://cookiepedia.co.uk/all-about-cookies'
            },
            cookie: {
                name: 'cookieconsent_demo',
                path: '/',
                domain: '',
                expiryDays: 1
            },
            elements: {
                messagelink: `<p id="cookieconsent:desc" class="cc-message">{{message}}
                    <a aria-label="learn more about cookies" tabindex="0" href="{{href}}" target="_blank" class="cc-link">{{link}}</a>
                </p>`,
                dismiss: '<button type="button" aria-label="Dismiss cookie message" tabindex="0" class="a-button a-button--secondary cc-btn cc-dismiss">{{dismiss}}</button>'
            }
        })
    ]
});

export class AppModule {};
```

```typescript
import { CookieconsentService } from '@acpaas-ui/ngx-layout';

constructor(
    private cookieconsentService: CookieconsentService
) {
    this.cookieconsentService.init({});
}
```

## Contributing

Visit our [Contribution Guidelines](../../../../../CONTRIBUTING.md) for more information on how to contribute.
