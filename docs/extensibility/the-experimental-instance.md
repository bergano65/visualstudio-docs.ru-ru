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
ms.openlocfilehash: 493ab672322db2826f8f7e7675decdda0a531538
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435070"
---
# <a name="the-experimental-instance"></a>Экспериментальный экземпляр
Для защиты среды разработки Visual Studio из непроверенных приложений, которые можно изменить его, VSSDK предоставляет экспериментальный пространства, который можно использовать для экспериментов. Разработать новые приложения с помощью Visual Studio как обычно, но их можно выполнить с помощью этого экспериментальный экземпляр.

 Каждое приложение, имеет пакет VSIX запустится экспериментальный экземпляр Visual Studio в режиме отладки.

 Если вы хотите запустить экспериментальный экземпляр Visual Studio за пределами специальное решение, выполните следующую команду в окне командной строки:

 "*\<Путь установки visual studio >* \Common7\IDE\devenv.exe «RootSuffix Exp

> [!NOTE]
> Экспериментальный экземпляр записывается в раздел реестра `<version number>Exp` и `<version number>Exp_Config` узлов. Приведен пример области экспериментальный реестра Visual Studio 2015
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` и `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Мы рекомендуем запустить расширение в экспериментальном экземпляре при его разработке. При развертывании расширения, он выполняется в экземпляре разработки. Дополнительные сведения о регистрации приложений, см. в разделе [регистрации пакетов VSPackage](../extensibility/internals/registering-vspackages.md).