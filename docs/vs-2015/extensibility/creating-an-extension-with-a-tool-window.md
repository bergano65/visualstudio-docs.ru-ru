---
title: Создание расширения с окном инструментов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afa24a7faceade36cf6b3d19c7e86fb8d6676ba8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559161"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Создание расширения с помощью окна инструментов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [создания расширения с окном инструментов](https://docs.microsoft.com/visualstudio/extensibility/creating-an-extension-with-a-tool-window).  
  
В этой процедуре вы узнаете, как использовать шаблон проекта VSIX и **окно инструментов Custom** шаблона элемента для создания расширения с окном инструментов.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Создание окна инструментов  
  
1.  Создайте проект VSIX с именем **FirstWindow**. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, в разделе **Visual C# / Extensibility**.  
  
2.  При открытии проекта, добавьте код шаблона элемента окна инструментов с именем **FirstWindow**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C# / Extensibility** и выберите **собственное окно средства**. В **имя** в нижней части окна, измените имя файла окно инструмента для **FirstWindow.cs**.  
  
3.  Выполните сборку решения и запустите отладку.  
  
     Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения о экспериментальный экземпляр, см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
4.  В экспериментальном экземпляре выберите **представления / Other Windows**.  
  
     Вы увидите пункт меню для **FirstWindow**. Щелкните его.  
  
     Вы должны увидеть окно инструментов с заголовком **FirstWindow** и появится кнопка с надписью **Click Me!.**

