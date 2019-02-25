# Alt-svc

Header-ul pentru serviciul alternativ (Alt-svc) și cadrul corespondent din HTTP/2,
`ALT-SVC` nu au fost create special pentru QUIC sau HTTP/3. Ele sunt parte a 
unui sistem deja proiectat și creat pentru ca un server să îi poată spune unei 
aplicații-client: *"uite, rulez același serviciu pe ACEASTĂ GAZDĂ, folosind 
ACEST PROTOCOL, pe ACEST PORT"*. Vedeți mai multe detalii în [RFC 
7838](https://tools.ietf.org/html/rfc7838).

Un client care primește un astfel de răspuns Alt-svc este, apoi, sfătuit, 
dacă implementează și dorește, să se conecteze la cealaltă gazdă folosită în 
paralel în fundal - folosind protocolul specificat - și, dacă schimbul reușește, 
să își schimbe toate operațiile pe acelea în loc de conexiunea inițială.

Dacă conexiunea inițială folosește HTTP/2 sau chiar HTTP/1, server-ul poate 
răspunde și să îi spună clientului că se poate conecta înapoi și să încerce 
HTTP/3. Poate fi către aceeași gazdă sau către o alta care știe cum să servească 
cererea originală. Informația oferită într-un astfel de răspuns Alt-svc are un 
timp de expirare, făcând ca clienții să poată să redirecționeze conexiuni și 
cereri ulterioare către gazdă alternativă folosind protocolul alternativ sugerat, 
pentru o anumită perioadă de timp.

## Exemplu

Un server HTTP include un header `Alt-Svc` în răspunsul său:

    Alt-Svc: h3=":50781"

Asta indică că HTTP/3 este disponibil pe port-ul UDP 50781, pe același nume de 
gazdă care a fost folosit pentru a primi acest răspuns.

Un client poate apoi să încerce să stabilească o conexiune QUIC către acea 
destiație și, dacă reușește, să continuie să comunice cu acea origin așa în loc 
de versiunea HTTP originală.
