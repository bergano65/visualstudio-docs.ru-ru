---
title: "Экспериментальный экземпляр | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Экспериментальные построений"
  - "Пакеты VSPackage, экспериментальной сборки"
  - "VSIP экспериментальной сборки"
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 36
caps.handback.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
---
# Экспериментальный экземпляр
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Для защиты среды разработки Visual Studio из непроверенных приложений, которые можно изменить его, VSSDK предоставляет экспериментальном пространства, который можно использовать для экспериментирования. Разработка новых приложений с помощью Visual Studio, как обычно, но запускать их с помощью этого экспериментальный экземпляр.  
  
 Каждое приложение, пакет VSIX запускается в экспериментальном экземпляре Visual Studio в режиме отладки.  
  
 Если вы хотите запустить экспериментальный экземпляр Visual Studio за пределами конкретного решения, выполните следующую команду в командной строке:  
  
 «*\< путь установки visual studio \>*\\Common7\\IDE\\devenv.exe «RootSuffix Exp  
  
> [!NOTE]
>  Экспериментальный экземпляр записывается в разделе реестра `<version number>Exp` и `<version number>Exp_Config` узлов. Примером является область экспериментальном реестра Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` и `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`.  
  
 Рекомендуется запустить расширение в экспериментальном экземпляре во время разработки. При развертывании расширения, оно выполняется в экземпляре разработки. Дополнительные сведения о регистрации приложения в разделе [Регистрация пакеты VSPackage](../extensibility/internals/registering-vspackages.md).