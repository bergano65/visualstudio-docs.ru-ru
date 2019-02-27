---
title: Регистрация расширений платформы .NET Framework | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bf1eb0001ca7c8b87fa44b5ea861df9d9fcba84d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644345"
---
# <a name="register-extensions-of-the-net-framework"></a>Регистрация расширений платформы .NET Framework
Можно создать сборку, расширяющую определенную версию платформы .NET Framework. Чтобы отобразить сборку в диалоговом окне Visual Studio **Добавление ссылок**, необходимо добавить ее родительскую папку в системный реестр.

 Например, предположим, что компания Trey Research разработала библиотеку, которая расширяет платформу .NET Framework 4. При этом сборки библиотеки должны отображаться в диалоговом окне **Добавление ссылок** при разработке проекта для платформы .NET Framework 4. Также предположим, что сборки установлены в папке *C:\TreyResearch\Extensions4\\*, являются 64-разрядными и выполняются на 64-разрядном компьютере или являются 32-разрядными и выполняются на 32-разрядном компьютере.

 Зарегистрируйте эту папку с помощью следующего раздела: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**. Присвойте этому разделу значение по умолчанию: **C:\TreyResearch\Extensions4**.

> [!NOTE]
>  Номер сборки версии .NET Framework может быть другим.

 Чтобы зарегистрировать 32-разрядную сборку на 64-разрядном компьютере, используйте узел Wow6432, например: **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**.

### <a name="see-also"></a>См. также
- [интеграция Visual Studio](../msbuild/visual-studio-integration-msbuild.md);