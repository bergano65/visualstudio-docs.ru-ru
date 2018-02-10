---
title: "Установка Visual Studio SDK | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8a5a4721eea178e4a9ab5766760ccf1405589684
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="installing-the-visual-studio-sdk"></a>Установка Visual Studio SDK
Пакет SDK для Visual Studio является дополнительным компонентом в программе установки Visual Studio. VS SDK также можно установить позже.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Установка Visual Studio SDK в процессе установки Visual Studio  
 Если вы хотите включить в установку Visual Studio на СТРАНИЦЕ, следует установить **разработки расширения Visual Studio** рабочей нагрузки в разделе **другие наборы средств**. Будет выполнена установка Visual Studio SDK, а также все необходимые условия. Выполнить более глубокую настройку установки, выбрав или сняв выделение компонентов из сводки представления. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Установка Visual Studio SDK после установки Visual Studio  
 Если вы решили установить пакет SDK для Visual Studio после завершения установки Visual Studio, повторно запустите установщик Visual Studio и выберите **разработки расширения Visual Studio** рабочей нагрузки.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Установка Visual Studio SDK из решения  
 Если открыть решение с проектом расширения без необходимости установки на СТРАНИЦЕ, будет приглашение, выделенная информационное выше в обозревателе решений. Он должен выглядеть примерно следующим образом:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Установка из командной строки Visual Studio SDK  
Как и в Visual Studio рабочей нагрузки или компонента, можно также установить этот элемент из командной строки. В разделе [использовать параметры командной строки для установки Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) подробные сведения о параметрах командной строки, соответствующие и способ определения идентификаторов рабочей нагрузки или компонента.
  
 Обратите внимание, что необходимо использовать установщик Visual Studio, который соответствует установленной версии Visual Studio. Например при наличии Visual Studio Enterprise, установленной на компьютере, необходимо запустить программу установки Visual Studio Enterprise (vs_enterprise.exe).