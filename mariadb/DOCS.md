# Home Assistant Add-on: MariaDB

## Installation

Follow these steps to get the add-on installed on your system:

1. Navigate in your Home Assistant frontend to **Supervisor** -> **Add-on Store**.
2. Find the "MariaDB" add-on and click it.
3. Click on the "INSTALL" button.

## How to use

1. Set the `logins` -> `password` field to something strong and unique.
2. Start the add-on.
3. Check the add-on log output to see the result.
4. Add `recorder` component to your Home Assistant configuration.

## Add-on Configuration

The MariaDB server add-on can be tweaked to your likings. This section
describes each of the add-on configuration options.

Example add-on configuration:

```yaml
databases:
  - homeassistant
logins:
  - username: homeassistant
    password: PASSWORD
rights:
  - username: homeassistant
    database: homeassistant
```

### Option: `databases` (required)

Database name, e.g., `homeassistant`. Multiple are allowed.

### Option: `logins` (required)

This section defines a create user definition in MariaDB. [Create User][createuser] documentation.

### Option: `logins.username` (required)

Database user login, e.g., `homeassistant`. [User Name][username] documentation.

### Option: `logins.password` (required)

Password for user login. This should be strong and unique.

### Option: `rights` (required)

This section grant privileges to users in MariaDB. [Grant][grant] documentation.

### Option: `rights.username` (required)

This should be the same user name defined in `logins` -> `username`.

### Option: `rights.database` (required)

This should be the same database defined in `databases`.

## Home Assistant Configuration

MariaDB will be used by the `recorder` and `history` components within Home Assistant. For more information about setting this up, see the [recorder integration][mariadb-ha-recorder] documentation for Home Assistant.

Example Home Assistant configuration:

```yaml
recorder:
  db_url: mysql://homeassistant:password@core-mariadb/homeassistant?charset=utf8
```

## Support

Got questions?

You have several options to get them answered:

- The [Home Assistant Discord Chat Server][discord].
- The Home Assistant [Community Forum][forum].
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

In case you've found a bug, please [open an issue on our GitHub][issue].

[createuser]: https://mariadb.com/kb/en/library/create-user
[username]: https://mariadb.com/kb/en/library/create-user/#user-name-component
[hostname]: https://mariadb.com/kb/en/library/create-user/#host-name-component
[grant]: https://mariadb.com/kb/en/library/grant
[mariadb-ha-recorder]: https://www.home-assistant.io/integrations/recorder/
[discord]: https://discord.gg/c5DvZ4e
[forum]: https://community.home-assistant.io
[i386-shield]: https://img.shields.io/badge/i386-yes-green.svg
[issue]: https://github.com/home-assistant/hassio-addons/issues
[reddit]: https://reddit.com/r/homeassistant
[repository]: https://github.com/hassio-addons/repository
