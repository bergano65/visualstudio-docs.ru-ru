---
title: Экспериментальный экземпляр | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2284767a0aa6be58c0f7e38c912783728914cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699038"
---
# <a name="the-experimental-instance"></a>Экспериментальный экземпляр
Чтобы защитить среду разработки Visual Studio от нетестируемых приложений, которые могут изменить его, VSSDK предоставляет экспериментальное пространство, которое можно использовать для эксперимента. Вы разрабатываете новые приложения с помощью Visual Studio обычным образом, но они выполняются с помощью этого экспериментального экземпляра.

 Каждое приложение с пакетом VSIX запускает экспериментальный экземпляр Visual Studio в режиме отладки.

 Если вы хотите запустить экспериментальный экземпляр Visual Studio за пределами определенного решения, выполните в командном окне следующую команду:

 *\<Visual studio installation path>* Exp "\Common7\IDE\devenv.exe"/рутсуффикс

> [!NOTE]
> Экспериментальный экземпляр записывается в реестр на `<version number>Exp` узлах и `<version number>Exp_Config` . Например, в экспериментальной области реестра Visual Studio 2015
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` и `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Мы рекомендуем запускать расширение в экспериментальном экземпляре при разработке. При развертывании расширения оно выполняется в экземпляре разработки. Дополнительные сведения о регистрации приложений см. в разделе [Регистрация пакетов VSPackage](../extensibility/internals/registering-vspackages.md).
