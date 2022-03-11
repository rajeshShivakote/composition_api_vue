option Api                                     Composition Api

1) data() { ... }                              1) ref(), reactive()
2) methods: { doSmth() { ... }}                2) function doSmth() { ... }
3) computed: { val() { ... }}                  3) const val = computed()
4) watch: { ... }                              4) watch( dep, (new, old) => {})
5) provide: { ... }/ inject: []                5) provide(key, val),
                                                  inject(key)