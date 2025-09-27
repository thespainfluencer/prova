addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request))
})

async function handleRequest(request) {
  // URL del sito da cui prendere i contenuti
  const target = 'https://thespainfluencer.com'

  // Ricostruisci URL della richiesta originale
  const url = new URL(request.url)
  const targetUrl = target + url.pathname + url.search

  // Inoltra la richiesta al sito di destinazione
  const response = await fetch(targetUrl, {
    method: request.method,
    headers: request.headers
  })

  // Copia la risposta
  const newHeaders = new Headers(response.headers)
  newHeaders.set('Access-Control-Allow-Origin', '*') // opzione se serve CORS

  return new Response(await response.text(), {
    status: response.status,
    statusText: response.statusText,
    headers: newHeaders
  })
}
