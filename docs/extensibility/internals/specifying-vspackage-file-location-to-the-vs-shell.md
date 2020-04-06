---
title: Указание местонахождения файла VSPackage в оболочку VS (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704980"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Выбор расположения файла VSPackage к оболочке Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]должны быть в состоянии найти сборку DLL для загрузки VSPackage. Вы можете найти его по-разному, как описано в следующей таблице.

| Метод | Описание |
| - | - |
| Используйте ключ реестра CodeBase. | Ключ CodeBase может быть [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использован для прямого загрузки сборки VSPackage с любого полностью квалифицированного пути файла. Значение ключа должно быть путь файла к DLL. Это лучший способ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загрузить сборку пакета. Этот метод иногда называют "CodeBase / частный метод каталога установки". Во время регистрации значение кодовой базы передается классам <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> атрибутов регистрации через экземпляр типа. |
| Поместите DLL в каталог **PrivateAssemblies.** | Поместите сборку в субдиректоре [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Каталога PrivateAssemblies.** Сборки, расположенные в **PrivateAssemblies,** автоматически обнаруживаются, но не видны в диалоговом окне **Добавления ссылок.** Разница между **PrivateAssemblies** и **PublicAssemblies** заключается в том, что собрания в **публичных собраниях** перечисляются в диалоговом окне **Добавления ссылок.** Если вы решили не использовать технику "CodeBase/private installation directory", то следует установить в каталог **PrivateAssemblies.** |
| Используйте сильно названную сборку и ключ реестра Ассамблеи. | Ключ сборки может быть использован [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для явного прямого для загрузки сильной названной сборки VSPackage. Ценность ключа должна быть сильным названием сборки. |
| Поместите DLL в каталог **PublicAssemblies.** | Наконец, сборка также может быть помещена в субдиректорию **PublicAssemblies.** Сборки, расположенные в **PublicAssemblies,** автоматически обнаруживаются, а также появятся в диалоговом окне **Add References** в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Сборки VSPackage должны быть помещены в каталог **PublicAssemblies** только в том случае, если они содержат управляемые компоненты, предназначенные для повторного использования другими разработчиками VSPackage. Большинство собраний не отвечают этому критерию. |

> [!NOTE]
> Используйте прочные, подписанные сборки для всех зависимых собраний. Эти сборки также должны быть установлены в вашем собственном каталоге или кэше глобальной сборки (GAC). Это защищает от конфликтов с сборками, которые имеют то же базовое имя файла, известное как связывание слабого имени.
