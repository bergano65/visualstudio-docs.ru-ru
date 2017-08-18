---
title: "Рекомендации по использованию API среды выполнения Windows | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime API
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: 693b3dac9def5533417638c3ec1c0de8db1d5fe3
ms.contentlocale: ru-ru
ms.lasthandoff: 08/11/2017

---
# <a name="considerations-when-using-the-windows-runtime-api"></a>Рекомендации по использованию API среды выполнения Windows
Практически все элементы API среды выполнения Windows можно использовать в JavaScript. Однако при этом необходимо учитывать ряд аспектов их представления.  
  
> [!IMPORTANT]
>  Сведения о создании компонентов среды выполнения Windows в C++, C# и Visual Basic, а также об их использовании в JavaScript см. в разделах [Создание компонентов среды выполнения Windows в C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) и [Создание компонентов среды выполнения Windows в C# и Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="special-cases-in-the-javascript-representation-of-windows-runtime-types"></a>Особые случаи в представлении типов среды выполнения Windows в JavaScript  
  
-   Строки: неинициализированная строка передается в метод среды выполнения Windows в виде строки "undefined", а строка с назначением `null` — в виде строки "null". (Это справедливо для случаев, в которых значения `null` или `undefined` приводятся к строке.) Прежде чем передать строку в метод среды выполнения Windows, инициализируйте ее как пустую строку ("").  
  
-   Интерфейсы: реализовать интерфейс среды выполнения Windows в JavaScript невозможно.  
  
-   Массивы: в среде выполнения Windows изменение размеров массивов не допускается, поэтому изменяющие размеры массивов методы из JavaScript с массивами среды выполнения Windows работать не будут.  
  
-   Массивы: если передать значение массива JavaScript в метод среды выполнения Windows, массив будет скопирован. Метод среды выполнения Windows не может изменить массив или его элементы и затем вернуть массив в приложение JavaScript. Однако вы можете использовать типизированные массивы (например, [объект Int32Array](../javascript/reference/int32array-object.md)), которые не копируются.  
  
-   Структуры: структуры среды выполнения Windows в JavaScript представляют собой объекты. Если вы хотите передать структуру среды выполнения Windows в метод среды выполнения Windows, не создавайте экземпляр структуры с помощью ключевого слова `new`. Вместо этого создайте объект и добавьте нужные элементы и их значения. Имена элементов должны указываться в "верблюжьем" стиле: `SomeStruct.firstMember`.  
  
-   Объекты: объекты JavaScript отличаются от объектов управляемого кода (`System.Object`). Вы не можете передать объект JavaScript в метод среды выполнения Windows, для которого требуется `System.Object`.  
  
-   Идентичность объекта: в большинстве случаев объекты, передаваемые между JavaScript и средой выполнения Windows, не изменяются. Подсистема JavaScript хранит карту известных объектов. При возвращении объекта из среды выполнения Windows он сравнивается с картой, и если этого объекта не существует в карте, создается новый объект. Те же действия выполняются для объектов, которые представляют интерфейсы, возвращаемые методами среды выполнения Windows. Из этого правила есть два исключения:  
  
    -   Объекты, которые возвращаются в результате вызова среды выполнения Windows и получают новые свойства (expando), не сохраняют новые свойства при передаче обратно в среду выполнения Windows. Тем не менее, когда эти объекты возвращаются приложению JavaScript, они не имеют свойств expando, так как возвращаемые объекты сравниваются с существующими объектами.  
  
    -   Структуры и делегаты в среде выполнения Windows не идентичны структурам или делегатам, использованным ранее. Каждый раз при возвращении структуры или делегата возвращается новая ссылка.  
  
-   Конфликты имен: несколько интерфейсов среды выполнения Windows могут иметь элементы с одинаковыми именами. Если они объединены в один объект JavaScript (который может быть представлением класса или интерфейса среды выполнения), то элементы представляются полностью допустимыми именами. Эти элементы можно вызывать с помощью следующего синтаксиса: `Class["MemberName"](parameter)`.  
  
     В следующем коде два интерфейса имеют метод Draw, а класс среды выполнения реализует оба интерфейса.  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     Вот как можно вызвать приведенный выше код в JavaScript.  
  
    ```JavaScript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   Параметры `Out`: если метод среды выполнения Windows имеет несколько параметров `out`, в JavaScript этот метод возвращает объект JavaScript, который имеет свойства, соответствующие параметру `out`. Например, рассмотрим следующую сигнатуру метода среды выполнения Windows в C++.  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     Версия этой сигнатуры для JavaScript:  
  
    ```JavaScript  
    var returnValue = exampleMethod();  
  
    ```  
  
     В этом примере `returnValue` — объект JavaScript, у которого будет два поля: `first` и `second`.  
  
-   Статические элементы: в среде выполнения Windows определяются как статические элементы, так и элементы экземпляров. В JavaScript в объект, связанный с классом или интерфейсом среды выполнения Windows, добавляются статические элементы.  
  
    ```JavaScript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Дополнительные сведения о представлении базовых типов среды выполнения Windows в JavaScript см. в разделе [Представление типов среды выполнения Windows в JavaScript](../jswinrt/javascript-representation-of-windows-runtime-types.md).
