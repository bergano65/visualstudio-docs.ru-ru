---
title: Экспериментальный экземпляр | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ee3c1ef0aed082a0e4e0fb519c744fda376fc8e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842536"
---
# <a name="the-experimental-instance"></a>Экспериментальный экземпляр
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы защитить среду разработки Visual Studio от нетестируемых приложений, которые могут изменить его, VSSDK предоставляет экспериментальное пространство, которое можно использовать для эксперимента. Вы разрабатываете новые приложения с помощью Visual Studio обычным образом, но они выполняются с помощью этого экспериментального экземпляра.  
  
 Каждое приложение с пакетом VSIX запускает экспериментальный экземпляр Visual Studio в режиме отладки.  
  
 Если вы хотите запустить экспериментальный экземпляр Visual Studio за пределами определенного решения, выполните в командном окне следующую команду:  
  
 *\<Visual studio installation path>* Exp "\Common7\IDE\devenv.exe"/рутсуффикс  
  
> [!NOTE]
> Экспериментальный экземпляр записывается в реестр на `<version number>Exp` узлах и `<version number>Exp_Config` . Например, в экспериментальной области реестра Visual Studio 2015  
>   
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` и `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Мы рекомендуем запускать расширение в экспериментальном экземпляре при разработке. При развертывании расширения оно выполняется в экземпляре разработки. Дополнительные сведения о регистрации приложений см. в разделе [Регистрация пакетов VSPackage](../extensibility/internals/registering-vspackages.md).
