---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "Изменение порядка параметров-рефакторинг (C#) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.reorder
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3469e9ae7101c9e180fba5558fce389c6dfcc72d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="reorder-parameters-refactoring-c"></a>Рефакторинг для упорядочения параметров (C#)
`Reorder Parameters`Visual C# операции рефакторинга, который предоставляет простой способ изменения порядка параметров методов, индексаторов и делегатов. `Reorder Parameters`Изменяет объявление, и во всех местах, где вызывается член, параметров изменяется в соответствии с новым порядком.  
  
 Для выполнения `Reorder Parameters` операции, поместите курсор на или рядом с метод, индексатор или делегата. Если курсор находится в положении, вызывать `Reorder Parameters` операции, нажав сочетание клавиш или выбрав соответствующую команду в контекстном меню.  
  
> [!NOTE]
>  Невозможно изменить порядок первого параметра метода расширения.  
  
### <a name="to-reorder-parameters"></a>Изменение порядка параметров  
  
1.  Создание библиотеки классов с именем `ReorderParameters`, а затем замените `Class1` следующий пример кода.  
  
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
  
2.  Поместите курсор на `MethodB`, в объявлении метода или вызов метода.  
  
3.  На **рефакторинг** меню, нажмите кнопку **изменение порядка параметров**.  
  
     **Изменение порядка параметров** откроется диалоговое окно.  
  
4.  В **изменение порядка параметров** выберите `int i` в **параметры** списка и нажмите кнопку «вниз».  
  
     Кроме того, можно перетащить `int i` после `bool b` в **параметры** списка.  
  
5.  В **изменение порядка параметров** диалоговое окно, нажмите кнопку **ОК**.  
  
     Если **Предварительный просмотр изменений ссылок** выбран параметр **изменение порядка параметров** диалоговом **Предварительный просмотр изменений — изменение порядка параметров** появится диалоговое окно. Он обеспечивает Предварительный просмотр изменений в списке параметров для `MethodB` в сигнатуре и вызова метода.  
  
    1.  Если **Предварительный просмотр изменений — изменение порядка параметров** диалоговое окно, нажмите кнопку **применить**.  
  
         В этом примере в объявлении метода и метод вызова сайтов для `MethodB` обновляются.  
  
## <a name="remarks"></a>Примечания  
 Можно изменить порядок параметров в объявлении метода или вызов метода. Поместите курсор на или рядом с объявление метода или делегата, но не в тексте.  
  
## <a name="see-also"></a>См. также  
 [Рефакторинг (C#)](refactoring-csharp.md)