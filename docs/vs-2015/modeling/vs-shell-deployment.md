---
title: Развертывание VS Shell | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e1a1bd92d1a0b91aa01d940695cd780f7e63c098
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572430"
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [развертывание VS Shell](https://docs.microsoft.com/visualstudio/modeling/vs-shell-deployment).  
  
Изолированной оболочки позволяет определить, какие Visual Studio функциональные возможности, вам понадобится взаимодействовать с вашего доменного языка и как это решение должно выглядеть. Дополнительные сведения о изолированная оболочка Visual Studio, см. в разделе [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md). Можно найти дополнительные сведения о настройке изолированной оболочки в [Настройка изолированной оболочки](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Чтобы задать оболочку Visual Studio в качестве цели развертывания  
  
1.  В **DslPackage** откройте проект **source.extension.tt**.  
  
2.  В разделе `<SupportedProducts>` вставки:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Замените *MyIsolatedShell* с именем пакета изолированной оболочки.



