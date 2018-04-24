---
title: L2DBForm.xaml.cs Source Code
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: sample
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c74e5f8df3d79a81ba15bed10169f45add14728
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="l2dbformxamlcs-source-code"></a>L2DBForm.xaml.cs Source Code

Этот раздел включает содержимое и описание исходного кода C# в файле L2DBForm.xaml.cs. Разделяемый класс L2XDBForm, содержащийся в этом файле, можно разбить на три логических раздела: элементы данных и обработчики событий `OnRemove` и `OnAddBook`.

## <a name="data-members"></a>Элементы данных

Для обеспечения связи этого класса с ресурсами окна из L2DBForm.xaml используются два закрытых элемента данных.

-   Переменная пространства имен `myBooks` инициализируется значением `"http://www.mybooks.com"`.

-   Элемент `bookList` инициализируется в конструкторе строкой CDATA из L2DBForm.xaml с помощью следующего кода:

    ```
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a>Обработчик события OnAddBook

В этом методе содержатся следующие три инструкции.

-   Первая условная инструкция используется для проверки правильности ввода.

-   Во второй инструкции создается элемент <xref:System.Xml.Linq.XElement> из строковых значений, введенных пользователем в разделе пользовательского интерфейса **Add New Book**.

-   В третьей инструкции происходит добавление этого нового элемента в поставщик данных L2DBForm.xaml. Следовательно, благодаря динамической привязке данных происходит автоматическое обновление пользовательского интерфейса с учетом этого нового элемента, поэтому дополнительный пользовательский код не требуется.

## <a name="onremove-event-handler"></a>Обработчик события OnRemove

Обработчик события `OnRemove` сложнее обработчика события `OnAddBook` по двум причинам. Во-первых, необработанный код XML содержит сохраненные пробелы, поэтому в записи книги следует также удалить соответствующие символы перевода строки. Во-вторых, выделение, которое относилось к удаленному элементу, для удобства переустанавливается на предыдущий элемент в списке.

Но основная работа по удалению выделенного элемента выполняется только двумя инструкциями.

-   Вначале извлекается элемент книги, связанный с выделенным в настоящее время пунктом в окне списка.

    ```
    XElement selBook = (XElement)lbBooks.SelectedItem;
    ```

-   Затем этот элемент удаляется из поставщика данных.

    ```
    selBook.Remove();
    ```

И в этом случае динамическая привязка данных обеспечивает автоматическое обновление пользовательского интерфейса программы.

## <a name="example"></a>Пример

### <a name="code"></a>Код

```csharp
using System;
using System.Linq;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Input;
using System.Xml;
using System.Xml.Linq;

namespace LinqToXmlDataBinding {
    /// <summary>
    /// Interaction logic for L2XDBForm.xaml
    /// </summary>

    public partial class L2XDBForm : System.Windows.Window
    {
        XNamespace mybooks = "http://www.mybooks.com";
        XElement bookList;

        public L2XDBForm()
        {
            InitializeComponent();
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
        }

        void OnRemoveBook(object sender, EventArgs e)
        {
            int index = lbBooks.SelectedIndex;
            if (index < 0) return;

            XElement selBook = (XElement)lbBooks.SelectedItem;
            //Get next node before removing element.
            XNode nextNode = selBook.NextNode;
            selBook.Remove();

            //Remove any matching newline node.
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))
            { nextNode.Remove(); }

            //Set selected item.
            if (lbBooks.Items.Count > 0)
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }
        }

        void OnAddBook(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(tbAddID.Text) ||
                String.IsNullOrEmpty(tbAddValue.Text))
            {
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");
                return;
            }
            XElement newBook = new XElement(
                                mybooks + "book",
                                new XAttribute("id", tbAddID.Text),
                                tbAddValue.Text);
            bookList.Add("  ", newBook, "\r\n");
        }
    }
}

```

### <a name="comments"></a>Комментарии

Сведения о связанном источнике данных XAML для этих обработчиков см. в статье [L2DBForm.xaml Source Code](../designers/l2dbform-xaml-source-code.md) (Исходный код L2DBForm.xaml)

## <a name="see-also"></a>См. также

- [Пошаговое руководство. Пример LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Исходный код L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)