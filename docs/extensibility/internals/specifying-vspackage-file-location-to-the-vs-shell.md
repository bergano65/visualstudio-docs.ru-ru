---
title: Выбор расположения файла VSPackage к оболочке VS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a1a28232b276456dd2b9a982533e1974ed9a088
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932419"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Выбор расположения файла VSPackage к оболочке Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] должен иметь возможность найти сборку библиотеки DLL для загрузки VSPackage. Его можно найти различными способами, как описано в следующей таблице.  


| Метод | Описание |
| - | - |
| Используйте раздел реестра CodeBase. | Ключ базы кода может использоваться для направления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для загрузки VSPackage сборки из любого полное имя пути. Значение ключа должно содержать путь файла к библиотеке DLL. Это лучший способ иметь [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загрузить сборку пакета. Этот способ иногда называют «CodeBase и закрытого directory методика установки.» Во время регистрации значение базы кода, передается в качестве атрибута классов регистрации через экземпляр <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> типа. |
| Поместите библиотеки DLL в **PrivateAssemblies** каталога. | Поместите сборку в **PrivateAssemblies** подкаталог [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] каталога. Сборки расположены в **PrivateAssemblies** определяются автоматически, но не отображаются в **Add References** диалоговое окно. Разница между **PrivateAssemblies** и **PublicAssemblies** является то, что сборки в **PublicAssemblies** перечислены в **Добавление ссылок**  диалоговое окно. Если вы решили не использовать метод «каталог установки базы кода/private», то следует установить в **PrivateAssemblies** каталога. |
| Используйте является сборкой со строгим именем и ключ реестра сборки. | Ключ сборки можно использовать для явного перенаправления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для загрузки со строгим именем сборки VSPackage. Значение ключа должно быть строгое имя сборки. |
| Поместите библиотеки DLL в **PublicAssemblies** каталога. | Наконец, сборку можно также поместить **PublicAssemblies** подкаталог. Сборки расположены в **PublicAssemblies** автоматически обнаруживаются, а также будут отображаться в **Add References** диалогового окна в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Сборки VSPackage должен быть помещен только в **PublicAssemblies** каталог, если они содержат управляемых компонентов, которые предназначены для повторного использования другими разработчиками VSPackage. Большинство сборок не соответствуют этому критерию. |

> [!NOTE]
>  Использование сборок со строгим именем, с подписью для все зависимые сборки. Эти сборки также должны быть установлены на собственного каталога или глобальном кэше сборок (GAC). Это обеспечивает защиту от конфликтует со сборками, имеющими то же имя базового файла, известный как weak имя привязки.