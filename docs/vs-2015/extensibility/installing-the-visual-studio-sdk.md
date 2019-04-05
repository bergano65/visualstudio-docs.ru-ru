---
title: Установка пакета SDK для Visual Studio | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 796d5f3f233310157b0784e213b81237e767055b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992142"
---
# <a name="installing-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Установка пакета SDK для Visual Studio как часть установки Visual Studio  
 Если вы хотите включить в установку Visual Studio на СТРАНИЦЕ, необходимо выполнить выборочную установку.  
  
> [!NOTE]
>  В исполняемый файл установки называется Visual Studio SDK **средств расширения Visual Studio**.  
  
1.  Запустите программу установки Visual Studio 2015. Вы можете установить любой выпуск Visual Studio, кроме Express.  
  
2.  На первом экране выберите **Custom**, а не **по умолчанию**. Нажмите кнопку **Далее**.  
  
3.  Вы увидите древовидное представление пользовательских функций. Откройте **Общие средства**. Вы должны увидеть **средств расширения Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  Проверьте **средств расширения Visual Studio** , затем нажмите кнопку **Далее** и продолжить установку.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Установка пакета SDK для Visual Studio после установки Visual Studio  
 Если вы решили установить пакет SDK для Visual Studio после завершения установки Visual Studio, необходимо выполнить следующую процедуру:  
  
1.  Перейдите к **панель управления / программы / программы и компоненты**и найдите **Visual Studio 2015**. Вы можете установить Visual Studio SDK для любого выпуска Visual Studio 2015, кроме Express.  
  
2.  Щелкните правой кнопкой мыши **Visual Studio 2015**, а затем нажмите кнопку **изменение**. Вы увидите страницу установки.  
  
3.  Выполните ту же процедуру, как показано на **установка Visual Studio SDK как часть установки Visual Studio** выше.  
  
4.  Нажмите кнопку **средств расширения Visual Studio** ссылку, чтобы установить пакет SDK для Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Установка пакета SDK для Visual Studio из решения  
 При открытии решения с проектом расширения без предварительной установки на СТРАНИЦЕ, вам будет предложено полосой выделенные сведения выше в обозревателе решений. Он должен выглядеть примерно следующим образом:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Установка пакета SDK для Visual Studio из командной строки  
 VSSDK можно установить из командной строки с помощью **переключатель/installselectableitems** переключиться с установщиком Visual Studio. Дополнительные сведения об использовании параметров командной строки с установщиком, см. в разделе [установка Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Вот как можно установить на СТРАНИЦЕ, автоматически с помощью установщика Visual Studio 2015 Community:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Обратите внимание на то, что необходимо использовать установщик Visual Studio, который соответствует установленной версии Visual Studio. Например если у вас есть Visual Studio Enterprise, установленной на компьютере, необходимо запустить установщик Visual Studio Enterprise (vs_enterprise.exe).
