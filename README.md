# LINQJOIN Projesi

Bu C# konsol uygulaması, yazarlar ve kitaplar arasında ilişki kurarak LINQ ile eşleşen verileri listeler.

## 🚀 Amaç

- `Author` ve `Book` sınıflarıyla örnek veriler oluşturmak  
- `Join` kullanarak kitap ve yazarları eşleştirmek  
- Sadece eşleşen kayıtları göstermek  

## 🧾 Veri Yapısı

**Yazarlar (Authors):**

- AuthorId (int)
- Name (string)

**Kitaplar (Books):**

- BookId (int)
- Title (string)
- AuthorId (int)

Bazı yazarların hiç kitabı yok, bazı kitapların yazarı listede yoktur. Bu sayede `Join`'in nasıl çalıştığı daha net görülür.

## 🔍 LINQ Join Kullanımı

```csharp
var together = authors.Join(
    books,
    author => author.AuthorId,
    book => book.AuthorId,
    (author, book) => new
    {
        bookName = book.Title,
        authorName = author.Name
    });

foreach (var item in together)
{
    Console.WriteLine($"Kitap: {item.bookName}, Yazar: {item.authorName}");
}
