---
title: "Развертывание в VS оболочки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 26b5075c36b152ecc44d65428521e191e6053609
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell

Изолированная оболочка позволяет определить, какие Visual Studio функциональности необходимо взаимодействовать с доменный язык и отображением этого решения. Дополнительные сведения о Visual Studio изолированной оболочки см. в разделе [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Для установки оболочки Visual Studio в качестве цели развертывания
  
1.  В **DslPackage** откройте проект **source.extension.tt**.  
  
2.  В разделе `<SupportedProducts>` вставки:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Замените *MyIsolatedShell* с именем пакета изолированной оболочки.