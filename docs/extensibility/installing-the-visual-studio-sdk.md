---
title: "Установка Visual Studio SDK | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9c25532605613b34ded15a4bd6a533e589b7fce2
ms.openlocfilehash: d039c50cea2ee038baec26fad02a98ae45f0d521
ms.lasthandoff: 02/22/2017

---
# <a name="installing-the-visual-studio-sdk"></a>Установка Visual Studio SDK
Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Установка Visual Studio SDK в процессе установки Visual Studio  
 Если вы хотите включить в установку Visual Studio VSSDK, необходимо выполнить выборочную установку.  
  
> [!NOTE]
>  В исполняемый файл установки Visual Studio SDK называется **средств расширения Visual Studio**.  
  
1.  Запустите программу установки Visual Studio 2015. Можно установить любой выпуск Visual Studio, за исключением Express.  
  
2.  На первом экране выберите **пользовательские**, а не **по умолчанию**. Нажмите кнопку **Далее**.  
  
3.  Вы увидите дерево пользовательских функций. Откройте **распространенных средств**. Вы должны увидеть **средств расширения Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  Проверьте **средств расширения Visual Studio** , нажмите кнопку **Далее** и продолжить установку.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Установка пакета SDK для Visual Studio после установки Visual Studio  
 Если вы решили установить пакет SDK для Visual Studio после завершения установки Visual Studio, необходимо выполните следующую процедуру.  
  
1.  Последовательно выберите пункты **панели управления или программы и программы и компоненты**и найдите **Visual Studio 2015**. Можно установить пакет Visual Studio SDK для любой выпуск Visual Studio 2015, за исключением Express.  
  
2.  Щелкните правой кнопкой мыши **Visual Studio 2015**, а затем нажмите кнопку **изменить**. Вы увидите страницу установки.  
  
3.  Выполните ту же процедуру, как и в **установка Visual Studio SDK как часть установки Visual Studio** выше.  
  
4.  Щелкните **средств расширения Visual Studio** ссылку, чтобы установить пакет SDK для Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Установка Visual Studio SDK из решения  
 При открытии решения в проекте расширения без необходимости установки VSSDK, вам предложат по выделенным информационное выше в обозревателе решений. Он должен выглядеть примерно следующим образом:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Установка из командной строки Visual Studio SDK  
 VSSDK можно установить из командной строки с помощью **/InstallSelectableItems** переключиться с установщиком Visual Studio. Дополнительные сведения об использовании параметров командной строки с помощью установщика см [использовать параметры командной строки для установки Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).  
  
 Вот как можно установить VSSDK, без вмешательства пользователя с помощью установщика Visual Studio Community 2015 г.:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Обратите внимание, что необходимо использовать установщик Visual Studio, которая соответствует установленной версии Visual Studio. Например если у вас есть Visual Studio Enterprise, установленной на компьютере, необходимо запустить установщик Visual Studio Enterprise (vs_enterprise.exe).
