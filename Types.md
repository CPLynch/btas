
ECMAscript standarzes the format of types but JS engines will not nessarcarily use that format in reality but will use whatever format is most performant as long as the outward behaviour matches what is expected exactly.

Why is NaN === NaN // false. Because typeof NaN === 'number', NaN is dissallowed from equalling any number type in the spec. 

string.length returns the number of code units used by the UTF-16 encoding to create the string. An emoticon like \uD83D\uDE0A as a surrogte pair would increase the length by two. A work around is to spread the string into an array and then call length on that.
