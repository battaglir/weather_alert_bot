SOURCE_URL:="https://api.weather.gov/alerts/active?zone=ORZ023,ORZ021,ORZ022,ORZ024,ORZ025,ORZ026,ORZ027,ORZ028,ORZ029,ORZ030,CAZ101,CAZ102,CAZ080,CAZ081,CAZ083,CAZ084,CAZ103,CAZ105,CAZ107,CAZ082,CAZ013,CAZ014,CAZ104,CAZ106,CAZ108,CAZ063,CAZ015,CAZ066,CAZ063&status=actual"
# SOURCE_URL:="https://s3.amazonaws.com/media.johnkeefe.net/data/example_warnings.json"

all: clean download slack

clean:
	-rm ./tmp/download.json

download:
	-mkdir tmp
	wget --continue --progress=dot:mega --waitretry=60 ${SOURCE_URL} \
		--header='accept: application/geo+json' \
		--header='User-Agent: (ijpr.org, battaglir@sou.edu)' \
		-O tmp/download.json

warnings:
	node warnings.js

slack:
	node warnings-slack.js
