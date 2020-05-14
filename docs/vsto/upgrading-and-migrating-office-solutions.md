---
title: Обновление и перенос решений Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e421d6e4ee94d9974c0a0583db1fb495c72593e
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416540"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Обновление и перенос решений Office
  Если проект Microsoft Office был создан в более ранней версии Visual Studio, его необходимо обновить для использования в текущей версии Visual Studio. Чтобы обновить проект Microsoft Office, откройте его в версии Visual Studio, имеющей в своем составе инструменты разработчика Microsoft Office. Для получения дополнительной информации о версиях Visual Studio, которые включают в себя инструменты разработчика Microsoft Office, [см.](../vsto/configuring-a-computer-to-develop-office-solutions.md)

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Visual Studio не может обновлять проекты шаблонов форм InfoPath, созданные с помощью предыдущих версий Visual Studio. Проекты этого типа в текущей версии Visual Studio не поддерживаются.

## <a name="changes-to-upgraded-projects"></a>Изменения в обновленных проектах
 При обновлении проекта Microsoft Office среда Visual Studio вносит изменения в проект, чтобы обеспечить ориентацию на следующие элементы:

- Визуальная студия 2010 Инструменты для управления время выполнения. Для получения дополнительной информации смотрите [обзор Visual Studio Tools for Office.](../vsto/visual-studio-tools-for-office-runtime-overview.md)

- Ссылки текущей сборки.

- Версия платформы .NET Framework, поддерживаемая типом проекта (только при обновлении до Visual Studio 2013).

- Версия Microsoft Office, поддерживаемая типом проекта (только при обновлении до Visual Studio 2013).

## <a name="assembly-references"></a>Ссылки на сборки
 Visual Studio обновляет следующие ссылки на сборки в проекте:

- Основные сборки взаимодействия Microsoft Office (PIA).

- Сборки в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Для получения дополнительной информации об [Visual Studio Tools for Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)этих сборках см.

- Новые или обновленные версии зависимых сборок.

## <a name="targeted-net-framework"></a>Версия .NET Framework, на которую производится ориентация
 При обновлении проекта до Visual Studio 2013 среда Visual Studio вносит изменения в проект, чтобы ориентироваться на [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] или [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Версия платформы .NET Framework, на которую производится ориентация проекта, зависит от того, какая версия Office установлена на компьютере. Если установлена [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] , Visual Studio ориентирует проект на [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. В противном случае Visual Studio ориентирует проект на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

> [!NOTE]
> При запуске переориентированного решения на компьютере разработчика или конечного пользователя могут потребоваться некоторые дополнительные действия. Кроме того, проект может перестать компилироваться, если в нем используются некоторые функции. Для получения дополнительной информации [см. решения Migrate Office в рамках .NET 4 или позже.](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)

 Если вы ориентируете проект Office на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, то можете использовать некоторые функции, недоступные для .NET Framework 3.5. Для получения дополнительной информации [см.](../vsto/designing-and-creating-office-solutions.md)

## <a name="targeted-office-application"></a>Целевое приложение Office
 При обновлении проекта Office до Visual Studio 2013 среда Visual Studio ориентирует проект на версию Microsoft Office, поддерживаемую типом проекта, например проектом настройки на уровне документа или проектом надстройки VSTO.

 Проекты Office в Visual Studio 2013 могут ориентироваться на приложения [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] . Visual Studio изменяет проект с целью ориентации на последнюю установленную версию Office. Если ни одна из этих версий Office не установлена, Visual Studio не обновляет проект.

> [!NOTE]
> При обновлении проекта VSTO Add-in для [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] целевой `ThisAddIn_Startup` или более поздней, убедитесь, что обработчик событий add-in VSTO не содержит кода, который получает доступ к документу в приложении. Для получения дополнительной информации смотрите [документ Access, когда приложение Office запускается.](../vsto/programming-vsto-add-ins.md#AccessingDocuments)

 Для настройки на уровне [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] документов преобразует документы в проект, имеющем двоичный формат, например документы с расширением *.xls* или *.doc,* в формат Office Open XML. Для получения дополнительной информации об Open XML см. Введение в [новые расширения имя файла и форматы Open XML](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).

> [!NOTE]
> Не рекомендуется использовать смарт-теги в Excel 2010 и Word 2010. Таким образом, если в решении используются смарт-теги, их необходимо удалить перед началом тестирования и отладки в Visual Studio 2013 или Visual Studio 2015.

## <a name="upgrade-microsoft-office-2003-projects"></a>Обновление проектов Microsoft Office 2003
 При обновлении настроек на уровне документа и надстроек VSTO, предназначенных для Microsoft Office 2003, необходимо учитывать дополнительные факторы.

### <a name="document-level-projects"></a>Проекты на уровне документов
 Если документ в проекте содержит элементы управления Windows Forms, то перед обновлением проекта необходимо убедиться, что установлена среда выполнения набора средств Visual Studio 2005 для Office (второй выпуск). Если эта версия среды выполнения не будет установлена на компьютере разработчика перед обновлением проекта, то обновленный проект может содержать ошибки компиляции или ошибки времени выполнения. После завершения обновления проекта можно удалить среду выполнения набора средств Visual Studio 2005 для Office (второй выпуск) с компьютера разработчика, если она не используется другими решениями Office. Эта версия среды выполнения доступна в виде распространяемого пакета в Центре загрузки Майкрософт на странице [Среда выполнения набора средств Microsoft Visual Studio 2005 для Office (второй выпуск) (VSTO 2005 SE) (x86)](https://www.microsoft.com/download/details.aspx?id=2392).

### <a name="vsto-add-in-projects"></a>Проекты надстроек VSTO
 Если файл решения для исходного проекта содержал проект установки или проект InstallShield Limited Edition, настроенный на установку надстройки VSTO, среда Visual Studio обновляет проект, но не вносит в него никаких изменений. Если вы хотите продолжать использовать файл установщика Windows для развертывания надстройки VSTO, необходимо внести в проект установки или проект InstallShield Limited Edition изменения, касающиеся установки новых необходимых компонентов, таких как [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], среда выполнения набора средств Visual Studio 2010 для Office и, при необходимости, основных сборок взаимодействия, на которые есть ссылки в надстройке VSTO. Для получения дополнительной информации [см. Развертывание решения Office с помощью установки Windows.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

 Если вы хотите использовать ClickOnce для развертывания надстройки VSTO, можно полностью удалить проект установки или проект InstallShield Limited Edition. Для получения дополнительной информации о развертывании надсытов VSTO с помощью ClickOnce [см.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>См. также раздел
- [Как: Обновление офисных решений](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)
- [Миграция решений Office в рамках .NET 4 или позже](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Обновление проекта, диалоговая коробка вариантов](../vsto/project-upgrade-options-dialog-box.md)
