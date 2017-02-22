---
title: "Развертывание VS Shell | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Развертывание VS Shell
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Изолированная оболочки позволяет определить, какая функциональные возможности Visual Studio, необходимые для взаимодействия с доменным языком и это решение должно отображаться.  Дополнительные сведения об оболочке изолированной Visual Studio см. в разделе [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md).  Дополнительные сведения о том, как настраивать изолированную оболочку in [Настраивать изолированную оболочку](http://msdn.microsoft.com/ru-ru/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### Установка оболочку Visual Studio как целевой объект развертывания  
  
1.  в **DslPackage** открытый проект  **source.extension.tt**.  
  
2.  Под `<SupportedProducts>` insert:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Заменить MyIsolatedShell с именем изолированного пакета оболочки.