---
title: "Развертывание в VS оболочки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: e7632b99d3fa9d347b5a259cd446edc2f6d9efa8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell
Изолированная оболочка позволяет определить, какие Visual Studio функциональности необходимо взаимодействовать с доменный язык и отображением этого решения. Дополнительные сведения о Visual Studio изолированной оболочки см. в разделе [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md). Можно найти дополнительные сведения о настройке изолированной оболочки в [Настройка изолированной оболочки](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Для установки оболочки Visual Studio в качестве цели развертывания  
  
1.  В **DslPackage** откройте проект **source.extension.tt**.  
  
2.  В разделе `<SupportedProducts>` вставки:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Замените *MyIsolatedShell* с именем пакета изолированной оболочки.