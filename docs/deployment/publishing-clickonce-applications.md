---
title: Публикация приложений ClickOnce | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0c6f931af213ff7ce97ec77c2b742d6767cf733
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079256"
---
# <a name="publish-clickonce-applications"></a>Публикация приложений ClickOnce
При первой публикации приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] установка свойств публикации выполняется с помощью мастера публикации. В мастере доступно только несколько свойств. Для всех остальных свойств устанавливаются значения по умолчанию.  
  
 Последующие изменения свойств публикации выполняются на **публикации** странице в **конструктор проектов**.  
  
## <a name="publish-wizard"></a>мастер публикации  
 Мастер публикации можно использовать для настройки основных параметров для публикации приложения. В число этих свойств входят следующие.  
  
-   Расположение папки публикации — место, куда Visual Studio будет копировать файлы (локальный компьютер, общий сетевой файловый ресурс, FTP-сервер или веб-узел)  
  
-   Расположение папки установки — место, откуда пользователи будут выполнять установку (общий сетевой файловый ресурс, FTP-сервер, веб-узел, компакт- или DVD-диск)  
  
-   Доступность в оперативном или автономном режиме — возможность конечного пользователя обращаться к приложению при наличии или отсутствии подключения к сети  
  
-   Частота обновления — периодичность проверки на наличие новых обновлений.  
  
 Дополнительные сведения см. в разделе [как: публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Страница "Публикация"  
 Страница **Публикация** **конструктора проектов** используется для настройки свойств развертывания ClickOnce. В следующей таблице перечислены разделы.  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Практическое: Укажите, где Visual Studio копирует файлы](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Содержит сведения о выборе расположения, в котором Visual Studio размещает файлы приложения и манифесты.|  
|[Практическое: укажите расположение, где будет производиться Установка пользователями из](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Содержит сведения о выборе расположения для загрузки и установки приложения пользователями.|  
|[Практическое: укажите ClickOnce в автономный режим или режим Интернет-установки](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Содержит сведения о настройке режима доступности приложения — оперативного или автономного.|  
|[Практическое: Установка ClickOnce версии публикации](../deployment/how-to-set-the-clickonce-publish-version.md)|Описывает способ задания ClickOnce **версия публикации** свойство, которое определяет ли приложение, которое вы публикуете будет рассматриваться как обновление.|  
|[Практическое: автоматически ClickOnce увеличение номера версии публикации](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Описывается, как автоматически увеличивать номер редакции **PublishVersion** при каждой публикации приложения.|  
  
 Дополнительные сведения см. в разделе [страницы публикации, конструктор проектов](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Диалоговое окно "файлы приложения"  
 В этом диалоговом окне можно указать, способ категоризации файлов проекта для публикации, динамической загрузки и обновления. В нем находится таблица со списком файлов проекта, которые не исключены по умолчанию или имеют группу загрузки.  
  
 Исключение файлов, пометке файлов как файлов данных или необходимых компонентов и создании групп файлов для условной установки в пользовательском Интерфейсе Visual Studio, см. в разделе [как: Укажите, какие файлы публикуются с помощью ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Можно также пометить файлы данных с помощью средства Mage.exe. Дополнительные сведения см. в разделе [как: включение файла данных в приложении ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Диалоговое окно «Необходимые компоненты»  
 В этом диалоговом окне определяются установленные необходимые компоненты, а также способ их установки. Дополнительные сведения см. в разделе [как: Установка необходимых компонентов для приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) и [одноименном диалоговом окне](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Диалоговое окно обновления приложения  
 В этом диалоговом окне определяется способ проверки установкой приложения наличия обновлений. Дополнительные сведения см. в разделе [как: управление обновлениями для ClickOnce-приложения](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Параметры диалогового окна публикации  
 В диалоговом окне "Параметры публикации" задаются параметры развертывания приложения.  
  
|||  
|-|-|  
|[Практическое: изменение языка публикации для приложения ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Содержит сведения об указании языка и региональных параметров, соответствующих локализованной версии.|  
|[Практическое: задание имени в меню Пуск для приложения ClickOnce](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|Содержит сведения об изменении отображаемого имени для приложения ClickOnce.|  
|[Практическое: укажите ссылку для получения технической поддержки](../deployment/how-to-specify-a-link-for-technical-support.md)|Описывает способ задания **URL-адрес поддержки** свойство, которое определяет веб-страницы или общей папке, где пользователи могут получить сведения о приложении.|  
|[Практическое: укажите URL-адрес поддержки для определенных необходимых компонентов в развертывании ClickOnce](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|Демонстрирует процесс изменения манифеста приложения вручную для включения отдельных URL-адресов службы поддержки для каждого необходимого предварительного условия.|  
|[Практическое: задание страницы публикации для приложения ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Содержит сведения о создании и публикации веб-страницы по умолчанию (publish.htm) вместе с приложением.|  
|[Практическое: Настройка веб-страницы по умолчанию ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Содержит сведения о настройке веб-страницы, которая автоматически создается и публикуется вместе с приложением.|  
|[Практическое: Включение автозапуска при установке с компакт-диска](../deployment/how-to-enable-autostart-for-cd-installations.md)|Содержит сведения о включении функции автозапуска для автоматического запуска приложения ClickOnce при вставке носителя.|  
  
## <a name="related-tpics"></a>Связанные tpics  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Практическое: создание ассоциаций файлов для ClickOnce-приложения](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Содержит сведения о добавлении поддержки расширения имени файла в приложение ClickOnce.|  
|[Практическое: извлечение сведений строки запроса в интерактивном приложении ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Демонстрирует извлечение параметров, передаваемых в URL-адрес, используемый для запуска приложения ClickOnce.|  
|[Практическое: отключение активации ClickOnce-приложений по URL-адрес с помощью конструктора](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Описывает, как заставить пользователей для запуска приложения из **запустить** меню с помощью конструктора.|  
|[Практическое: отключение активации по URL-АДРЕСУ приложений ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Описывает, как заставить пользователей для запуска приложения из **запустить** меню.|  
|[Пошаговое руководство: Загрузка сборок по требованию с помощью API развертывания ClickOnce с помощью конструктора](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Содержит сведения о загрузке сборок приложения только при их первом использовании с помощью конструктора.|  
|[Пошаговое руководство: Загрузка сборок по требованию с помощью API развертывания ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Содержит сведения о загрузке сборок приложения только при их первом использовании приложением.|  
|[Пошаговое руководство: Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Содержит сведения о пометке вспомогательных сборок как необязательных и загрузке только тех сборок, которые необходимы клиентскому компьютеру для использования текущих параметров культуры.|  
|[Пошаговое руководство: Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Содержит сведения об использовании служебных программ .NET Framework для развертывания приложения ClickOnce.|  
|[Пошаговое руководство: Развертывание вручную приложения ClickOnce, которое не нуждается в повторном подписывании и сохраняет фирменную символику](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)|Содержит сведения об использовании служебных программ .NET Framework для развертывания приложения ClickOnce без повторной подписи манифестов.|  
|[Практическое: Настройка проекта для конкретной платформы](../ide/how-to-configure-projects-to-target-platforms.md)|Описывает процесс публикации для 64-разрядный процессор, изменив **целевой ЦП** или **целевая платформа** свойство в проекте.|  
|[Пошаговое руководство: Включение приложения ClickOnce на нескольких версий платформы .NET Framework](http://msdn.microsoft.com/en-us/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Содержит сведения об установке и запуске приложения ClickOnce на нескольких версиях платформы .NET Framework.|  
|[Пошаговое руководство: Создание пользовательского установщика для приложения ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Содержит сведения о создании настраиваемого установщика для установки приложения ClickOnce.|  
|[Практическое: публикация приложения WPF с включенными визуальными стилями](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Содержит пошаговые инструкции для устранения ошибки, которая появляется при попытке публикации приложения WPF с включенными визуальными стилями.|  
  
## <a name="see-also"></a>См. также  
 [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Справочные сведения ClickOnce](../deployment/clickonce-reference.md)