---
title: Экспериментальная инстанция Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699038"
---
# <a name="the-experimental-instance"></a>Экспериментальный экземпляр
Чтобы защитить среду разработки Visual Studio от непроверенных приложений, которые могут изменить ее, VSSDK предоставляет экспериментальное пространство, которое можно использовать для экспериментов. Вы разрабатываете новые приложения, используя Visual Studio, как обычно, но вы запустите их с помощью этого экспериментального экземпляра.

 Каждое приложение, которое имеет пакет VSIX запускает Visual Studio экспериментальный экземпляр в режиме отладки.

 Если вы хотите запустить экспериментальный экземпляр Visual Studio за пределами конкретного решения, запустите следующую команду в окне команды:

 "*\<Визуальная студия установки путь>*"Common7"IDE'devenv.exe" /RootSuffix Exp

> [!NOTE]
> Экспериментальный экземпляр занесена `<version number>Exp` `<version number>Exp_Config` в реестр под и узлами. Например, экспериментальная зона регистрации Visual Studio 2015
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` и `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Мы рекомендуем вам запустить расширение в экспериментальном экземпляре во время его разработки. При развертывании расширения оно выполняется в экземпляре разработки. Для получения дополнительной информации о регистрации заявок, [см.](../extensibility/internals/registering-vspackages.md)
