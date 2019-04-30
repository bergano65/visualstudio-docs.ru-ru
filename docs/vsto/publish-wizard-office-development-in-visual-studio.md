---
title: Мастер публикации (Разработка Office в Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7879ad7cf18c3d09fddbab3923296e0896688af9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447068"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Мастер публикации (Разработка Office в Visual Studio)
  Используйте **мастера публикации** копируемые файлы решения в указанном расположении, создать файлы манифеста и создать программу установки.

 Чтобы открыть этот мастер на **построения** меню, выберите **публикации** *SolutionName*. Вы можете также получить доступ к **мастера публикации** из **обозревателе решений**. Откройте контекстное меню для узла проекта, а затем выберите **публикации**.

 В приведенных ниже разделах описаны страницы мастера.

## <a name="where-do-you-want-to-publish-the-application"></a>Где вы хотите опубликовать приложение?
 **Укажите расположение для публикации этого приложения** требуется. Место публикации — это каталог где **мастера публикации** копирует файлы решения, такие как манифесты, сборки, временный сертификат и другие файлы из сборки. Вы должны иметь доступ на запись в этом каталоге.

 Введите расположение как путь к диску, файловый ресурс, FTP-узла или URL-адрес веб-сайта или нажмите **Обзор** кнопку, чтобы перейдите к расположению. Путь может быть в этих форматах:

- Абсолютный или относительный путь в стандарт Windows форматирования, такие как *C:\Deploy\MyApplication* или *\MyApplication*.

- Путь универсальными именами (UNC), такие как  *\\\ServerName\MyApplication\\*.

- URL-адрес веб-сайта, такие как http://www.microsoft.com/MyApplication.

  Расположение публикации по умолчанию — *http://localhost/projectname/* Если установлены службы IIS, или каталог publish\, если службы IIS не установлены.

> [!NOTE]
> Если компьютер работает под управлением Windows Vista, существуют дополнительные рекомендации. Необходимо быть администратором на компьютере Windows Vista для использования параметра локальной публикации. Кроме того, по умолчанию всегда является *публикации\\*  каталог, независимо от того, что у вас есть установлены службы IIS.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Что такое путь установки по умолчанию на компьютерах конечных пользователей?
 Путь установки является необязательным. Позже можно задать путь установки, если вы предпочитаете. Подробную информацию см. в разделе [Практическое руководство. Изменение пути установки решения Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

 Путь установки используется каталог, из которого конечный пользователь будет устанавливать настройку. Этот путь также будет использоваться решением для проверки на наличие обновлений. **Мастера публикации** не развернуть решение в это расположение, если путь не является таким же, как вы указали **укажите расположение для публикации этого приложения** поле на предыдущей странице.

 **Веб-узле** укажите URL-адрес, будет следовать конечным пользователям для установки решения.

 **Из общего ресурса UNC путь или файл** укажите UNC-путь, которая последует за конечным пользователям для установки решения.

 **Компакт-диска или DVD-диска** этот параметр не требуется другой путь установки.

 Visual Studio записать компакт-ДИСК или DVD-диска. Выходные данные на компакт-или DVD-диска необходимо скопировать вручную.

## <a name="see-also"></a>См. также
- [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Страница публикации в конструкторе проектов &#40;разработка решений Office в Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
