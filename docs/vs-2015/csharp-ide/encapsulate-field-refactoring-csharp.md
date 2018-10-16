---
title: Инкапсулировать поле рефакторинг (C#) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 35d7e03e30aa5301ee65f15a8591fbccd1de3fcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223552"
---
# <a name="encapsulate-field-refactoring-c"></a>Рефакторинг для инкапсуляции поля (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Инкапсулировать поле** операция рефакторинга позволяет быстро создать свойство из существующего поля и легко обновить код со ссылками на новое свойство.  
  
 Когда [поле](http://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) — [открытый](http://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), другие объекты имеют прямой доступ к этому полю и могут изменять его незаметно для объекта, которому принадлежит это поле. С помощью [свойства](http://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) инкапсуляция поля, можно запретить прямой доступ к полям.  
  
 Для создания нового свойства, **инкапсулировать поле** операция изменяет модификатор доступа для поля, которое нужно инкапсулировать для [частного](http://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)и затем создает [получить](http://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71)и [задать](http://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) методы доступа для этого поля. В некоторых случаях создается только метод доступа `get`, например, если поле объявляется доступным только для чтения.  
  
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
  
3.  На **рефакторинг** меню, щелкните **инкапсулировать поле**.  
  
     **Инкапсулировать поле** откроется диалоговое окно.  
  
     Можно также ввести сочетание клавиш CTRL + R, E, чтобы отобразить **инкапсулировать поле** диалоговое окно.  
  
     Щелкните правой кнопкой мыши курсор, пункты **рефакторинг**, а затем нажмите кнопку **инкапсулировать поле** для отображения **инкапсулировать поле** диалоговое окно.  
  
4.  Укажите параметры.  
  
5.  Нажмите клавишу ВВОД или щелкните **ОК** кнопки.  
  
6.  Если вы выбрали **Предварительный просмотр изменений ссылок** параметр, то **Предварительный просмотр изменений ссылок** откроется окно. Нажмите кнопку **применить** кнопки.  
  
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
 **Инкапсулировать поле** операции возможно, только если курсор находится в той же строке, что и объявление поля.  
  
 Для объявления относятся несколько полей **инкапсулировать поле** использует запятую в качестве границ между полями и инициирует рефакторинг в ближайшем к курсору поле и в той же строке, что курсор. Чтобы указать, какое поле нужно инкапсулировать, можно также выбрать имя этого поля в объявлении.  
  
 Код, который создается этой операцией рефакторинга, моделируется функцией фрагментов кода инкапсуляции поля. Фрагменты кода можно изменять. Дополнительные сведения см. в статье [Фрагменты кода](../ide/code-snippets.md).  
  
## <a name="see-also"></a>См. также  
 [Рефакторинг (C#)](../csharp-ide/refactoring-csharp.md)   
 [Фрагменты кода Visual C#](../ide/visual-csharp-code-snippets.md)