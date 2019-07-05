---
title: Отладка с помощью средства просмотра Store | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a76cd9b726e534271937cb67a8d3f946d4eb477
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433200"
---
# <a name="debugging-by-using-the-store-viewer"></a>Отладка с использованием средства просмотра хранилища
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В окне просмотра Store, можно проверить состояние *хранения* используемые [!INCLUDE[dsl](../includes/dsl-md.md)]. Средство просмотра Store отображает все элементы модели домена, которые находятся в конкретном магазине, а также свойства элемента и ссылки между элементами.  
  
## <a name="opening-store-viewer"></a>Средство просмотра открывающей Store  
 При нахождении в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] экспериментальной сборки, где экземпляр хранилища содержит сведения о модели необходимо остановить кода в точке останова. Откройте средство просмотра Store, введя следующую команду в **Интерпретация** окна:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
> Необходимо заменить `mystore` с именем экземпляра хранилища. Кроме того при добавлении пространства имен в коде, можно ввести команды для отображения средства просмотра Store без полного пространства имен:  
>   
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
> `…`  
>   
> `StoreViewer.Show(mystore);`  
  
 `Show` Метод имеет несколько перегрузок. Экземпляр хранилища или секции можно указать в качестве параметра.  
  
 Кроме того, можно поместить строку кода, отображается средство просмотра Store в любом месте в коде где параметр, передаваемый `Show` метод находится в области. Это действие откроет средство просмотра Store, когда строка кода выполняется как моментальный снимок содержимого хранилища.  
  
### <a name="using-store-viewer"></a>С помощью средства просмотра Store  
 Когда откроется средство просмотра Store, немодальное окно Windows Forms выглядит, как показано на следующем рисунке.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
Средство просмотра Store  
  
 Средство просмотра Store есть три области: левой, верхней правой области и нижней правой области. Левая панель – древовидное представление типов в `DomainDataDirectory` член хранилища. Разверните узел раздела, щелкните элемент в верхней правой области отображаются свойства этого элемента. Если элемент связан с другими элементами, дополнительные элементы отображаются в нижней правой области. Если дважды щелкнуть элемент в нижней правой области, элемент будет выделен в левой области.  
  
## <a name="see-also"></a>См. также  
 [Перемещение по модели и обновление модели в коде программы](../modeling/navigating-and-updating-a-model-in-program-code.md)
