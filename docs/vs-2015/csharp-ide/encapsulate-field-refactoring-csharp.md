---
title: Рефакторинг инкапсуляции поля (C#) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b4f5ddbe7eab925b06584f00b04bed3c74e9811
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667571"
---
# <a name="encapsulate-field-refactoring-c"></a>Рефакторинг для инкапсуляции поля (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Операция рефакторинга " **Инкапсуляция поля** " позволяет быстро создать свойство из существующего поля, а затем легко обновить код со ссылками на новое свойство.

 Если [поле](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) является [открытым](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), другие объекты имеют прямой доступ к этому полю и могут изменить его, не выявляя объект, которому принадлежит это поле. Используя [Свойства](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) для инкапсуляции этого поля, можно запретить прямой доступ к полям.

 Чтобы создать новое свойство, операция **инкапсуляции поля** изменяет модификатор доступа для поля, которое необходимо инкапсулировать на [частный](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8), а затем создает методы доступа [Get](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71) и [Set](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) для этого поля. В некоторых случаях создается только метод доступа `get`, например, если поле объявляется доступным только для чтения.

 Подсистема рефакторинга обновляет код ссылками на новое свойство в областях, указанных в разделе **Обновление ссылок** диалогового окна **Инкапсуляция поля** .

### <a name="to-create-a-property-from-a-field"></a>Создание свойства из поля

1. Создайте консольное приложение с именем `EncapsulateFieldExample`, а затем замените `Program` на следующий пример кода.

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

2. В [редакторе кода](../ide/writing-code-in-the-code-and-text-editor.md)поместите курсор в объявление на имя поля, которое необходимо инкапсулировать. В приведенном ниже примере поместите курсор на слово `width`:

    ```csharp
    public int width, height;
    ```

3. В меню **Рефакторинг** выберите пункт **Инкапсулировать поле**.

     Откроется диалоговое окно **Инкапсуляция поля** .

     Можно также ввести сочетание клавиш CTRL + R, E, чтобы открыть диалоговое окно **Инкапсуляция поля** .

     Можно также щелкнуть правой кнопкой мыши курсор, навести указатель на пункт **Рефакторинг**и выбрать пункт **Инкапсулировать поле** , чтобы открыть диалоговое окно **Инкапсуляция поля** .

4. Укажите параметры.

5. Нажмите клавишу ВВОД или кнопку **ОК** .

6. Если выбран параметр **Предварительный просмотр изменений ссылок** , откроется окно **Предварительный просмотр изменений ссылок** . Нажмите кнопку **Apply (применить** ).

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

## <a name="remarks"></a>Заметки
 Операция **инкапсуляции поля** возможна только в том случае, если курсор располагается в той же строке, что и объявление поля.

 Для объявлений, объявляющих несколько полей, **Инкапсуляция поля** использует запятую в качестве границы между полями и инициирует рефакторинг для поля, ближайшего к курсору, и на той же строке, что и курсор. Чтобы указать, какое поле нужно инкапсулировать, можно также выбрать имя этого поля в объявлении.

 Код, который создается этой операцией рефакторинга, моделируется возможностью фрагментов кода инкапсуляции поля. Фрагменты кода можно изменять. Для получения дополнительной информации см. [Code Snippets](../ide/code-snippets.md).

## <a name="see-also"></a>См. также раздел
 [C#](../csharp-ide/refactoring-csharp.md) [Фрагменты кода визуальной C# ](../ide/visual-csharp-code-snippets.md) рефакторинга ()