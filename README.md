# Lesti_Fpc

[![Latest Release][ico-version]][link-release]
[![Software License][ico-license]](LICENSE.md)
[![Build Status][ico-travis]][link-travis]
[![Coverage Status][ico-coverall]][link-coveralls]

Simple Magento Fullpagecache. The current documentation can be found
[here](https://gordonlesti.com/lesti-fpc-documentationversion-1-4-5/).

## Install

Several quick start options are available:
### Install manually
  * [Download the latest release](https://github.com/GordonLesti/Lesti_Fpc/releases/latest)
  * Unzip
  * Copy `app` directory into Magento

### Install with [modman](https://github.com/colinmollenhour/modman)

```bash
modman clone https://github.com/GordonLesti/Lesti_Fpc.git
```

### Install with [Magento Composer Installer](https://github.com/Cotya/magento-composer-installer)
  * add the requirement `gordonlesti/lesti_fpc`
```json
{
    "require": {
        "gordonlesti/lesti_fpc": "*"
    }
}
```

## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email info@gordonlesti.com instead of using the issue tracker.

## Credits

- [Gordon Lesti][link-author]
- [All Contributors][link-contributors]

## License

The Open Software License v. 3.0 (OSL-3.0). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/github/release/GordonLesti/Lesti_Fpc.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-OSL--3.0-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/GordonLesti/Lesti_Fpc/master.svg?style=flat-square
[ico-coverall]: https://img.shields.io/coveralls/GordonLesti/Lesti_Fpc/master.svg?style=flat-square

[link-release]: https://github.com/GordonLesti/Lesti_Fpc/releases/latest
[link-travis]: https://travis-ci.org/GordonLesti/Lesti_Fpc
[link-coveralls]: https://coveralls.io/r/GordonLesti/Lesti_Fpc
[link-author]: https://gordonlesti.com/
[link-contributors]: ../../contributors
=======
* Install manually:
    * Download latest version [here](https://github.com/GordonLesti/Lesti_Fpc/archive/master.zip)
    * Unzip
    * Copy `app` directory into Magento

## For module creators

You can now make your modules compatible with Lesti_Fpc by injecting configuration to it. There is no longer a need to manually configure handles and parameters in admin.

See this example, configuration goes in your config.xml

```xml
<config>
    <!--  // your modules normal config // -->

    <default>
        <lesti_fpc>
            <cache_actions>
                <cms_index_index />
                <right.reports.product.viewed />
            </cache_actions>
            <miss_uri_params>
                <limit><![CDATA[limit=/^([0-9]+)|(all)$/"]]></limit>
            </miss_uri_params>
        </lesti_fpc>
    </default>
</config>
```

The keys used have the same name as the fields in admin, possible keys are:

* cache_actions
* bypass_handles
* uri_params
* refresh_actions
* miss_uri_params
* dynamic_blocks
* lazy_blocks

If a tag does *not* contain a value (like ```cms_index_index``` above), the tagname is used. If it *does* contain a value, that value is used (like ```limit``` above). 
