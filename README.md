# google-api-clj

Singularity group fork of https://github.com/viebel/google-api-clj

## reasoning

The original repo is a bit older.
The ecosystem is moving towards builtin tooling.
Also I wanted to try make this lib compatible with graalvm.

## todo

- [x] Move to deps.edn
- [x] Fix core functions override warns from clojure 10.11
- [ ] Get rid of reflection
- [ ] Do not initialize classes, if building for graalvm
- [ ] Achieve graalvm compatibility


## Usage

add deps:


```clojure
        viebel/google-api-clj
        {:git/sha "328245bcfab3b46fa526de760e4182237ffd315f" :git/url "git@github.com:SingularityGroup/google-api-clj.git"}

```


```clojure
(def credential-path "<path-to-google-api-creds>.json")

(def google-client (create-google-client {:credential-path credential-path
                                            :scopes [:drive :spreadsheets]
                                            :application-name ""}))

(def sheets-service (sheets/make-service google-client))

(def my-spreadheet (sheets/create-spreadsheet
                      {:service sheets-service}
                      {:spreadsheet-properties/title "Showtime! repl test"}
                      [{:sheet-properties/title "Code bold!"}]))
```

also check playground.clj in this repo for a super Rich comment.
check the api namespaces + the google api docs.


## License

Copyright © 2019 FIXME

This program and the accompanying materials are made available under the
terms of the Eclipse Public License 2.0 which is available at
http://www.eclipse.org/legal/epl-2.0.

This Source Code may also be made available under the following Secondary
Licenses when the conditions for such availability set forth in the Eclipse
Public License, v. 2.0 are satisfied: GNU General Public License as published by
the Free Software Foundation, either version 2 of the License, or (at your
option) any later version, with the GNU Classpath Exception which is available
at https://www.gnu.org/software/classpath/license.html.
