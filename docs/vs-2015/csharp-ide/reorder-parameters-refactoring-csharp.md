---
title: Рефакторинг переупорядочения параметров (C#) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e39564fb108b63859620e2c4a650608cdf1e7e82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673147"
---
# <a name="reorder-parameters-refactoring-c"></a>Рефакторинг для упорядочения параметров (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` — Это операция рефакторинга на языке Visual C#, которая предоставляет простой способ изменения порядка параметров для методов, индексаторов и делегатов. `Reorder Parameters` изменяет объявление и в любом месте, где вызывается элемент, параметры переупорядочиваются в соответствии с новым порядком.

 Чтобы выполнить `Reorder Parameters` операцию, установите курсор на метод, индексатор или делегат или рядом с ним. Когда курсор находится в позиции, вызовите операцию, нажав сочетание клавиш `Reorder Parameters` , или выбрав команду в контекстном меню.

> [!NOTE]
> Нельзя изменить порядок первого параметра в методе расширения.

### <a name="to-reorder-parameters"></a>Изменение порядка параметров

1. Создайте библиотеку классов с именем `ReorderParameters` и замените на `Class1` Следующий пример кода.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. Поместите курсор на `MethodB` , либо в объявлении метода, либо в вызове метода.

3. В меню **Рефакторинг** выберите команду **изменить порядок параметров**.

     Откроется диалоговое окно **Переупорядочение параметров** .

4. В диалоговом окне **Переупорядочение параметров** выберите `int i` в списке **Параметры** , а затем нажмите кнопку вниз.

     Кроме того, можно перетаскивать `int i` после `bool b` в списке **параметров** .

5. В диалоговом окне **изменение порядка параметров** нажмите кнопку **ОК**.

     Если в диалоговом окне **Переупорядочение параметров** выбран параметр **Предварительный просмотр изменений ссылок** , откроется диалоговое окно **Просмотр изменений — изменение порядка параметров** . Он обеспечивает предварительный просмотр изменений в списке параметров для `MethodB` как в сигнатуре, так и в вызове метода.

    1. Если откроется диалоговое окно **Просмотр изменений — изменение порядка параметров** , нажмите кнопку **Применить**.

         В этом примере обновляются объявление метода и все сайты вызова метода для `MethodB` .

## <a name="remarks"></a>Remarks
 Можно изменить порядок параметров в объявлении метода или вызове метода. Поместите курсор на или рядом с объявлением метода или делегата, но не в тексте.

## <a name="see-also"></a>См. также:
 [Рефакторинг (C#)](../csharp-ide/refactoring-csharp.md)