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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 722c32c139d2f560fa6d10aba9fd8bac610f9f20
ms.lasthandoff: 03/07/2017

---
# <a name="installing-the-visual-studio-sdk"></a>Установка Visual Studio SDK
Пакет SDK для Visual Studio — это дополнительная функция в программе установки Visual Studio. VS SDK также можно установить позже.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Установка Visual Studio SDK в процессе установки Visual Studio  
 Если вы хотите включить в установку Visual Studio VSSDK, следует установить **разработка расширений Visual Studio** рабочей нагрузки в разделе **другие наборы инструментов**. Будет выполнена установка Visual Studio SDK, а также все необходимые условия. Дополнительно можно настроить установку, выбрав или сняв выделение компонентов из сводки представления. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Установка пакета SDK для Visual Studio после установки Visual Studio  
 Если вы решили установить пакет SDK для Visual Studio после завершения установки Visual Studio, перезапустите установщик Visual Studio, а затем выберите **разработка расширений Visual Studio** рабочей нагрузки.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Установка Visual Studio SDK из решения  
 При открытии решения в проекте расширения без необходимости установки VSSDK, вам предложат по выделенным информационное выше в обозревателе решений. Он должен выглядеть примерно следующим образом:  
  
 ![SolutionExplorerInstall](~/docs/extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Установка из командной строки Visual Studio SDK  
Как и в Visual Studio рабочей нагрузки или компонент, можно также установить этот элемент из командной строки. В разделе [использовать параметры командной строки для установки Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) сведения о коммутаторы соответствующую командную строку и способ определения идентификаторов рабочей нагрузки или компонента.
  
 Обратите внимание, что необходимо использовать установщик Visual Studio, которая соответствует установленной версии Visual Studio. Например если у вас есть Visual Studio Enterprise, установленной на компьютере, необходимо запустить установщик Visual Studio Enterprise (vs_enterprise.exe).
