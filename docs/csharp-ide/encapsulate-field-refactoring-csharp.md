---
redirect_url: /visualstudio/csharp-ide/refactoring/encapsulate-field
title: "Инкапсулировать поле оптимизации (C#) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: d587edebcea443e0bfff52004b128c70923470d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="encapsulate-field-refactoring-c"></a>Рефакторинг для инкапсуляции поля (C#)
**Инкапсулировать поле** операция рефакторинга позволяет быстро создать свойство из существующего поля и легко обновить код со ссылками на новое свойство.  
  
 Когда [поле](/dotnet/csharp/programming-guide/classes-and-structs/fields) — [открытый](/dotnet/csharp/language-reference/keywords/public), другие объекты имеют прямой доступ к этому полю и могут изменять его незаметно для объекта, которому принадлежит это поле. С помощью [свойства](/dotnet/csharp/programming-guide/classes-and-structs/properties) инкапсуляция поля, можно запретить прямой доступ к полям.  
  
 Для создания нового свойства **инкапсулировать поле** изменяет модификатор доступа для поля, которое нужно инкапсулировать, на [закрытый](/dotnet/csharp/language-reference/keywords/private), а затем создает [получить](/dotnet/csharp/language-reference/keywords/get)и [задать](/dotnet/csharp/language-reference/keywords/set) для этого поля методы доступа. В некоторых случаях создается только метод доступа `get`, например, если поле объявляется доступным только для чтения.  
  
 Подсистема рефакторинга обновляет код, добавляя ссылки на новое свойство в областях, указанных в **обновление ссылок** раздел **инкапсулировать поле** диалоговое окно.  
  
### <a name="to-create-a-property-from-a-field"></a>Создание свойства из поля  
  
1.  Создайте консольное приложение с именем `EncapsulateFieldExample`, а затем замените `Program` на следующий пример кода.  
  
    ```csharp  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2.  В [редактор кода](../ide/writing-code-in-the-code-and-text-editor.md), поместите курсор в объявление на имени поля, которое нужно инкапсулировать. В приведенном ниже примере поместите курсор на слово `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  На **рефакторинг** меню, нажмите кнопку **инкапсулировать поле**.  
  
     **Инкапсулировать поле** откроется диалоговое окно.  
  
     Можно также ввести сочетание клавиш CTRL + R, E, чтобы отобразить **инкапсулировать поле** диалоговое окно.  
  
     Щелкните правой кнопкой мыши курсор, пункты **рефакторинг**, а затем нажмите кнопку **инкапсулировать поле** для отображения **инкапсулировать поле** диалоговое окно.  
  
4.  Укажите параметры.  
  
5.  Нажмите клавишу ВВОД или щелкните **ОК** кнопки.  
  
6.  Если вы выбрали **Предварительный просмотр изменений ссылок** параметр, то **Предварительный просмотр изменений ссылок** открывается окно. Нажмите кнопку **применить** кнопки.  
  
     В исходном файле отображается следующий код методов доступа `get` и `set`:  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     Код в методе `Main` также обновляется и получает новое имя свойства `Width`.  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>Примечания  
 **Инкапсулировать поле** операция возможна только когда курсор располагается на той же строке, что и объявление поля.  
  
 Для объявления относятся несколько полей **инкапсулировать поле** используется запятая как граница между полями и инициирует рефакторинг в ближайшем к курсору поле и в той же строке, где находится курсор. Чтобы указать, какое поле нужно инкапсулировать, можно также выбрать имя этого поля в объявлении.  
  
 Код, который создается этой операцией рефакторинга, моделируется функцией фрагментов кода инкапсуляции поля. Фрагменты кода можно изменять. Дополнительные сведения см. в статье [Фрагменты кода](../ide/visual-csharp-code-snippets.md).  
  
## <a name="see-also"></a>См. также  
 [Рефакторинг (C#)](refactoring-csharp.md)   
 [Фрагменты кода Visual C#](../ide/visual-csharp-code-snippets.md)