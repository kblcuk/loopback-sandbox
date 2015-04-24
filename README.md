#loopback-sandbox

A repository for reproducing [LoopBack community issues][wiki-issues].

[wiki-issues]: https://github.com/strongloop/loopback/wiki/Reporting-issues

To pre-populate with data, run with `node .`, and then:

`
curl 'http://localhost:3000/api/Users' -H 'Origin: http://localhost:3000' -H 'Content-Type: application/json' -H 'Accept: application/json' --data-binary '{"email":"fjark.lanf@farln.do", "password": "password"}' --compressed

curl 'http://localhost:3000/api/Users/login' -H 'Origin: http://localhost:3000' -H 'Content-Type: application/json' -H 'Accept: application/json' --data-binary '{"email":"fjark.lanf@farln.do", "password": "password"}' --compressed

curl 'http://localhost:3000/api/Buses?access_token=_TOKEN_FROM_PREVIOUS_RESPONSE' -H 'Content-Type: application/json' -H 'Accept: application/json' --data-binary '{"model":"Double-Decker"}' --compressed

# Returns bus model
curl 'http://localhost:3000/api/Buses/1?access_token=_TOKEN_FROM_PREVIOUS_RESPONSE' -H 'Content-Type: application/json' -H 'Accept: application/json' --compressed

# Should get passengers, but doesn't?
curl 'http://localhost:3000/api/Buses/1/passengers?access_token=_TOKEN_FROM_PREVIOUS_RESPONSE' -H 'Content-Type: application/json' -H 'Accept: application/json' --compressed

# Should not count passengers
curl 'http://localhost:3000/api/Buses/1/passengers/count?access_token=_TOKEN_FROM_PREVIOUS_RESPONSE' -H 'Content-Type: application/json' -H 'Accept: application/json' --compressed
`
