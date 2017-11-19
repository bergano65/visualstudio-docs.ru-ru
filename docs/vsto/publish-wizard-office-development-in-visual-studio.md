---
title: "Мастер публикации (Разработка Office в Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
ms.assetid: 793314b6-b6a6-4509-8f1c-dd9466cf5190
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8eeb0a002e2d62b9066165a99ce474cf7a01a88f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Мастер публикации (разработка для Office в Visual Studio)
  Используйте **мастер публикации** для копирования файлов решения в указанном расположении, создать файлы манифеста и программу установки.  
  
 Чтобы открыть этот мастер на **построения** меню, выберите **публикации** *имя_решения*. Кроме того, доступны **мастер публикации** из **обозревателе решений**. Откройте контекстное меню узла проекта и выберите **публикации**.  
  
 В приведенных ниже разделах описаны страницы мастера.  
  
## <a name="where-do-you-want-to-publish-the-application"></a>Где вы хотите опубликовать приложение?  
 **Укажите расположение для публикации этого приложения**  
 Обязательный. Расположение публикации — это каталог где **мастер публикации** копирует файлы решения, такие как манифесты, сборки, временные сертификаты и другие файлы из сборки. Вы должны иметь доступ на запись в этом каталоге.  
  
 Введите расположение как путь к диску, общую папку, FTP-узла или URL-адрес веб-сайта или нажмите **Обзор** кнопку, чтобы перейти к расположению. Путь может быть в следующих форматах:  
  
-   Относительный или абсолютный путь в стандартном формате Windows, например C:\Deploy\MyApplication или \MyApplication.  
  
-   Путь соглашения об универсальных именах (UNC), такие как \\\ServerName\MyApplication\\.  
  
-   URL-адрес веб-сайта, например http://www.microsoft.com/MyApplication.  
  
 Расположение публикации по умолчанию — *http://localhost/projectname/* , если установлены службы IIS, или каталог publish\, если службы IIS не установлены.  
  
> [!NOTE]  
>  Если целевой компьютер работает под управлением Windows Vista, предусмотрены дополнительные действия. Должны быть права администратора на компьютере Windows Vista для использования параметра Локальные публикации. Кроме того, по умолчанию всегда является *публикации\\*  каталог, независимо от того, что у вас есть установлены службы IIS.  
  
## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Что такое путь установки по умолчанию на компьютерах конечных пользователей?  
 Путь установки является необязательным. Путь установки можно задать позже при необходимости. Дополнительные сведения см. в разделе [как: изменение пути установки решения Office](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 Путь установки — каталог, из которого конечный пользователь будет устанавливать настройку. Этот путь также будет использоваться решением для проверки на наличие обновлений. **Мастер публикации** не развертывает решение в указанном местоположении, если путь не совпадает с введенным в **укажите место публикации данного приложения** на предыдущей странице.  
  
 **С веб-сайта**  
 Укажите URL-адрес, который должны перейти пользователи, чтобы установить решение.  
  
 **В общем UNC-пути или файловом ресурсе**  
 Укажите UNC-путь, который должны перейти пользователи, чтобы установить решение.  
  
 **Компакт-диска или DVD-диска**  
 Этот параметр не требует путь установки.  
  
 Visual Studio записать компакт-ДИСК или DVD-диска. Выходные данные на компакт-или DVD-диска необходимо скопировать вручную.  
  
## <a name="see-also"></a>См. также  
 [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Публикация страницы, конструктор проектов &#40; разработка решений Office в Visual Studio &#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  