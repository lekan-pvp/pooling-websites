# pooling-websites
## Опрос веб-сайтов

    package main

    import (
      "fmt"
      "net/http"
    )

    var urls = []string{
      "http://www.google.com",
      "http://golang.org",
      "http://blog.golang.org",
    }

    func main() {
      // Выполняет HTTP-запрос HEAD для всех URL адресов и возвращает строку состояния HTTP или строку ошибки.
      for _, url := range urls {
        resp, err := http.Head(url)
        if err != nil {
          fmt.Println("Error:", url, err)
        }
        fmt.Println(url, ": ", resp.Status)
      }
    }


В программе выше мы импортируем пакет `net/http`(см. Строку 4 ). Опрашиваются все URL-адреса в массиве строк 
urls(определенном в строке 7). В строке 16 мы начинаем итерацию ***urls*** циклом `for-range`. В строке 17 
`http.Head()` каждому URL-адресу отправляется простой запрос, чтобы узнать, как они отреагируют. Подпись функции: 
`func Head(url string) (r *Response, err error)`. Когда возникает ошибка, мы печатаем ее в строке 19 . Если ошибок 
нет, в строке 21 печатается статус `resp`.
