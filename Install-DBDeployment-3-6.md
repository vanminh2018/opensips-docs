Title: openSIPS | Documentation / Database Deployment

URL Source: https://www.opensips.org/Documentation/Install-DBDeployment-3-6

Markdown Content:
##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Database Deployment

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Install-DBDeployment-3-5 "Database Deployment - 3.5") [3.4](https://www.opensips.org/Documentation/Install-DBDeployment-3-4 "Database Deployment - 3.4") Older versions: [3.3](https://www.opensips.org/Documentation/Install-DBDeployment-3-3 "Database Deployment - 3.3") [3.2](https://www.opensips.org/Documentation/Install-DBDeployment-3-2 "Database Deployment - 3.2") [3.1](https://www.opensips.org/Documentation/Install-DBDeployment-3-1 "Database Deployment - 3.1") [3.0](https://www.opensips.org/Documentation/Install-DBDeployment-3-0 "Database Deployment - 3.0") [2.4](https://www.opensips.org/Documentation/Install-DBDeployment-2-4 "Database Deployment - 2.4") [2.3](https://www.opensips.org/Documentation/Install-DBDeployment-2-3 "Database Deployment - devel") [2.2](https://www.opensips.org/Documentation/Install-DBDeployment-2-2 "Database Deployment - 2.2") [2.1](https://www.opensips.org/Documentation/Install-DBDeployment-2-1 "Database Deployment - devel") [1.11](https://www.opensips.org/Documentation/Install-DBDeployment-1-11 "Database Deployment - ver 1.11") [1.10](https://www.opensips.org/Documentation/Install-DBDeployment-1-10 "Database Deployment - ver 1.10") [1.9](https://www.opensips.org/Documentation/Install-DBDeployment-1-9 "Database Deployment - ver 1.9") [1.8](https://www.opensips.org/Documentation/Install-DBDeployment-1-8 "Database Deployment - ver 1.8") [1.7](https://www.opensips.org/Documentation/Install-DBDeployment-1-7 "Database Deployment - ver 1.7") [1.6](https://www.opensips.org/Documentation/Install-DBDeployment-1-6 "Database Deployment - ver 1.6") [1.5](https://www.opensips.org/Documentation/Install-DBDeployment-1-5 "Database Deployment - ver 1.5") [1.4](https://www.opensips.org/Documentation/Install-DBDeployment-1-4 "Database Deployment - ver 1.4")

**Database Deployment v3.6**

* * *

After installing your OpenSIPS, most likely you will need to also deploy a database that you could use for various reasons ( DB user authentication, persistent registrations, dialogs, etc ).

* * *

You can deploy the opensips database using the [opensips-cli](https://github.com/OpenSIPS/opensips-cli) tool. Before you do that, you should [install it](https://github.com/OpenSIPS/opensips-cli#install).

### 1.  Configuring OpenSIPS CLI

Open your OpenSIPS CLI configuration file and specify the following parameters:

*   `database_schema_path` - (defaults to `/usr/share/opensips/`) set it to `[Install_Path]/share/opensips/`
*   `database_url` - the URL to connect to your database (if not specified, you will be prompted for it during deploy)
*   `database_name` - (defaults to `opensips`) the database to use
*   `database_modules` - (defaults to standard modules) the modules you want to deploy.

You can find more information about the OpenSIPS CLI tool configuration [here](https://github.com/OpenSIPS/opensips-cli/blob/master/docs/modules/database.md#configuration).

**Note:** OpenSIPS CLI searches for its configuration files in `~/.opensips-cli.cfg`, `/etc/opensips-cli.cfg`, `/etc/opensips/opensips-cli.cfg`, but you can also specify your own configuration file using the `-f` parameter.

### 2.  Creating the Database

In order to create the `database_name` database that you have provisioned above, run

opensips-cli -x database create

Later, if you decide to add a new module, for example presence, simply call:

opensips-cli -x database add presence

You can also specify a different name for the database, for example `opensips_test`, using:

opensips-cli -x database create opensips\_test
