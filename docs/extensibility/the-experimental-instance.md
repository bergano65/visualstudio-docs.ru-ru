---
title: Экспериментальный экземпляр | Документация Майкрософт
description: Узнайте, как пакет SDK для Visual Studio предоставляет экспериментальное пространство для запуска нетестируемых приложений в режиме отладки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 728913596ce8c3947756906dffb144eecd3d71ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895275"
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
