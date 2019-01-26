---
title: Экспериментальный экземпляр | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f77770b799c3d437f9f1a223dfe8d5c139b65ee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966950"
---
# <a name="the-experimental-instance"></a>Экспериментальный экземпляр
Для защиты среды разработки Visual Studio из непроверенных приложений, которые можно изменить его, VSSDK предоставляет экспериментальный пространства, который можно использовать для экспериментов. Разработать новые приложения с помощью Visual Studio как обычно, но их можно выполнить с помощью этого экспериментальный экземпляр.  
  
 Каждое приложение, имеет пакет VSIX запустится экспериментальный экземпляр Visual Studio в режиме отладки.  
  
 Если вы хотите запустить экспериментальный экземпляр Visual Studio за пределами специальное решение, выполните следующую команду в окне командной строки:  
  
 "*\<Путь установки visual studio >* \Common7\IDE\devenv.exe «RootSuffix Exp  
  
> [!NOTE]
>  Экспериментальный экземпляр записывается в раздел реестра `<version number>Exp` и `<version number>Exp_Config` узлов. Приведен пример области экспериментальный реестра Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` и `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Мы рекомендуем запустить расширение в экспериментальном экземпляре при его разработке. При развертывании расширения, он выполняется в экземпляре разработки. Дополнительные сведения о регистрации приложений, см. в разделе [регистрации пакетов VSPackage](../extensibility/internals/registering-vspackages.md).