# geodbconverter

[ipgeobase.ru](http://ipgeobase.ru/cgi-bin/Archive.cgi) DB to MaxMind GeoLiteCity conversion utility

## Installation

    npm -g install geodbconverter

## Usage

To create GeoIP `GeoLiteCity-Blocks.csv` and `GeoLiteCity-Location.csv` files run command:

#### Command line

    geodbconverter [options] [outputDir]
    
Options:

    -h, --help                output usage information
    -V, --version             output the version number
    -d, --download-url [url]  ipgeobase.ru zip archive url (by default http://ipgeobase.ru/files/db/Main/geo_files.zip)
    -l, --local               Use local files without archive downloading
    -i, --ipblocks [path]     Used only with --cities option. It's path to local file with blocks of IP addresses if used with --local option. It's file name in archive if DB is downloaded from ipgeobase.ru. By default "cidr_optim.txt"
    -c, --cities [path]       Used only with --ipblocks option. It's path to local file with cities names if used with --local option. It's file name in archive if DB is downloaded from ipgeobase.ru. By default "cities.txt"
    --ipblocks-output [path]  IP blocks output file name (by default "GeoLiteCity-Blocks.csv")
    --cities-output [path]    Cities output file name (by default "GeoLiteCity-Location.csv")
    
Examples:

Download db from ipgeobase server, convert and save to current directory

    geodbconverter
    
Convert and save to custom directory

    geodbconverter ./converted/GeoLiteCityFiles
    
Download db from custom file

    geodbconverter ./source/cidr_optim.txt ./source/cities.txt ./converted/GeoLiteCityFiles
    

#### Local module

    var geodbconvert = require('geodbconverter');

    geodbconvert([options]);

Options:

    input   {String} - Zip-archive url (by default http://ipgeobase.ru/files/db/Main/geo_files.zip)
            or {Object} with params
                blocks   - Source blocks file (by default "cidr_optim.txt")
                location - Source location file (by default "cities.txt")
                
    output  {String} - Output directory
            or {Object} with params
                blocks   - IP blocks output file name (by default "GeoLiteCity-Blocks.csv")
                location - Cities output file name (by default "GeoLiteCity-Location.csv")

## Notes

To convert `.csv` files to `.dat` use [mteodoro/mmutils](https://github.com/mteodoro/mmutils).
