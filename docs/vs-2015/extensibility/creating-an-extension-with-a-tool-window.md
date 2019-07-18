---
title: Создание расширения с окном инструментов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431853"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Создание расширения с помощью окна инструментов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этой процедуре вы узнаете, как использовать шаблон проекта VSIX и **окно инструментов Custom** шаблона элемента для создания расширения с окном инструментов.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Создание окна инструментов  
  
1. Создайте проект VSIX с именем **FirstWindow**. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, в разделе **Visual C# / Extensibility**.  
  
2. При открытии проекта, добавьте код шаблона элемента окна инструментов с именем **FirstWindow**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C# / Extensibility** и выберите **собственное окно средства**. В **имя** в нижней части окна, измените имя файла окно инструмента для **FirstWindow.cs**.  
  
3. Выполните сборку решения и запустите отладку.  
  
     Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения о экспериментальный экземпляр, см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
4. В экспериментальном экземпляре выберите **представления / Other Windows**.  
  
     Вы увидите пункт меню для **FirstWindow**. Щелкните его.  
  
     Вы должны увидеть окно инструментов с заголовком **FirstWindow** и появится кнопка с надписью **Click Me!.**
