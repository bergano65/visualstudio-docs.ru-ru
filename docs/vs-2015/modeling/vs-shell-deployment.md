---
title: Развертывание VS Shell | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 323dd1242dcc598b5f30fdd24f37e305712d4d78
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172917"
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Изолированной оболочки позволяет определить, какие Visual Studio функциональные возможности, вам понадобится взаимодействовать с вашего доменного языка и как это решение должно выглядеть. Дополнительные сведения о изолированная оболочка Visual Studio, см. в разделе [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md). Можно найти дополнительные сведения о настройке изолированной оболочки в [Настройка изолированной оболочки](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Чтобы задать оболочку Visual Studio в качестве цели развертывания  
  
1.  В **DslPackage** откройте проект **source.extension.tt**.  
  
2.  В разделе `<SupportedProducts>` вставки:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Замените *MyIsolatedShell* с именем пакета изолированной оболочки.



