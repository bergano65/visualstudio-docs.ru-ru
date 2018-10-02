---
title: Экспериментальный экземпляр | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d819be41806e075de23dbfb5b5b3cded5bbeb40
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563494"
---
# <a name="the-experimental-instance"></a>Экспериментальный экземпляр
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [экспериментальный экземпляр](https://docs.microsoft.com/visualstudio/extensibility/the-experimental-instance).  
  
Для защиты среды разработки Visual Studio из непроверенных приложений, которые можно изменить его, VSSDK предоставляет экспериментальный пространства, который можно использовать для экспериментов. Разработать новые приложения с помощью Visual Studio как обычно, но их можно выполнить с помощью этого экспериментальный экземпляр.  
  
 Каждое приложение, имеет пакет VSIX запустится экспериментальный экземпляр Visual Studio в режиме отладки.  
  
 Если вы хотите запустить экспериментальный экземпляр Visual Studio за пределами специальное решение, выполните следующую команду в окне командной строки:  
  
 "*\<Путь установки visual studio >* \Common7\IDE\devenv.exe «RootSuffix Exp  
  
> [!NOTE]
>  Экспериментальный экземпляр записывается в раздел реестра `<version number>Exp` и `<version number>Exp_Config` узлов. Приведен пример области экспериментальный реестра Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` и `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`.  
  
 Мы рекомендуем запустить расширение в экспериментальном экземпляре при его разработке. При развертывании расширения, он выполняется в экземпляре разработки. Дополнительные сведения о регистрации приложений, см. в разделе [регистрации пакетов VSPackage](../extensibility/internals/registering-vspackages.md).

