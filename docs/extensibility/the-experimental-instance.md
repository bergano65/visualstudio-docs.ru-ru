---
title: "Экспериментальный экземпляр | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2de242ed974716b0ba00918d30bc2679a36420fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="the-experimental-instance"></a>Экспериментальный экземпляр
Для защиты среды разработки Visual Studio из непроверенных приложений, которые можно изменить его, VSSDK предоставляет экспериментальный пространства, который можно использовать для экспериментов. При разработке новых приложений с помощью Visual Studio обычным образом, но их можно выполнить с помощью этого экспериментальный экземпляр.  
  
 Каждое приложение, имеется пакет VSIX запустится экспериментальный экземпляр Visual Studio в режиме отладки.  
  
 Если вы хотите запустить экспериментальный экземпляр Visual Studio за пределами конкретного решения, выполните следующую команду в командную строку:  
  
 «*\<Путь установки visual studio >*\Common7\IDE\devenv.exe» RootSuffix Exp  
  
> [!NOTE]
>  Экспериментальный экземпляр записывается в раздел реестра `<version number>Exp` и `<version number>Exp_Config` узлов. Например — область экспериментальный реестра Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` и `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`.  
  
 Рекомендуется, чтобы запустить расширение в экспериментальном экземпляре во время разработки. При развертывании расширения, оно выполняется в экземпляре разработки. Дополнительные сведения о регистрации приложения см. в разделе [регистрации пакетов VSPackage](../extensibility/internals/registering-vspackages.md).