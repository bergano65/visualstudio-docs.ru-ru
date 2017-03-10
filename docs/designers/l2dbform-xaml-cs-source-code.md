---
title: "Исходный код L2DBForm.xaml.cs | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
caps.latest.revision: 2
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 753635060d71edf9d71e5919d00c9b566e16320d
ms.lasthandoff: 02/22/2017

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
  
-   Во второй инструкции создается новый элемент <xref:System.Xml.Linq.XElement> из строковых значений, введенных пользователем в разделе **Add New Book** пользовательского интерфейса.  
  
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
  
### <a name="description"></a>Описание  
  
### <a name="code"></a>Код  
  
```c#  
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
 [Walkthrough: LinqToXmlDataBinding Example](../designers/walkthrough-linqtoxmldatabinding-example.md)  (Пошаговое руководство. Пример LinqToXmlDataBinding)  
 [Исходный код L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)
