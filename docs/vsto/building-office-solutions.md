---
title: Создание решений Office
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8733c4e068bd7c4be2674e302707b81cc180cfd8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963247"
---
# <a name="build-office-solutions"></a>Создание решений Office
  Сборка и отладка проектов Office в принципе не отличается от сборки и отладки других типов проектов в Visual Studio, например Windows Forms. В этом разделе описываются существующие различия. Общие сведения о том, как создавать приложения, см. в разделе [компиляция и сборка в Visual Studio](../ide/compiling-and-building-in-visual-studio.md).

> [!NOTE]
>  Занимаетесь разработкой решений, расширяющих возможности Office по [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и вы можете создавать их с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.

## <a name="project-output-for-office-projects"></a>Выходные данные проекта для проектов Office
 Выходным каталогом проектов Office является каталог *имя_проекта*\bin\release или *имя_проекта*\bin\debug. Нельзя выполнять сборку в каталог развертывания.

### <a name="document-level-projects"></a>Проекты уровня документа
 При сборке проекта уровня документа в выходной каталог проекта включаются следующие элементы:

-   копия документа проекта;

-   сборка проекта и все связанные сборки, свойству **Копировать локально** которых присвоено значение **true**;

-   Манифест приложения, который имеет расширение имени файла *.manifest*. Дополнительные сведения см. в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

-   Манифест развертывания, который имеет расширение имени файла *.vsto*. Дополнительные сведения см. в разделе [манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md).

-   База данных программы (*PDB*) файла.

> [!NOTE]
>  Если сборка решения выполняется не на локальный компьютер, а в удаленное расположение, добавьте полный путь к нему в список надежных расположений в центре управления безопасностью приложения. Дополнительные сведения см. в разделе Присвоение уровня доверия документам в [решений Office, защита](../vsto/securing-office-solutions.md).

### <a name="application-level-projects"></a>Проекты уровня приложения
 При создании проекта надстройки VSTO, в выходных данных проекта включаются следующие элементы:

- сборка проекта и все связанные сборки, свойству **Копировать локально** которых присвоено значение **true**;

- Манифест приложения, который имеет расширение имени файла *.manifest*. Дополнительные сведения см. в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

- Манифест развертывания, который имеет расширение имени файла *.vsto*. Дополнительные сведения см. в разделе [манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md).

- База данных программы (*PDB*) файла для сборки проекта.

  При сборке проектов надстроек VSTO на компьютере разработчика также создаются записи в реестре, необходимые для загрузки надстройки VSTO. Дополнительные сведения см. в разделе [записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

  При сборке проекта надстройки Outlook VSTO, содержащего области формы, в реестр добавляются следующие дополнительные данные:

- Раздел для каждого класса сообщений, связанного с одной или несколькими областями формы.

- Запись для каждой области формы и соответствующее значение, представляющее имя надстройки Outlook VSTO.

  Приложение Outlook использует эту информацию для загрузки областей форм.

## <a name="referenced-assemblies"></a>Связанные сборки
 Вы можете ссылаться на сборки (включая проекты библиотеки классов) из проекта сборки решений Office. Каждая сборка, на которую существует ссылка, имеет свойство **Копировать локально**. Свойство**Копировать локально** указывает, копируется ли сборка в выходной каталог. По умолчанию для этого свойства установлено значение **true**. Каждая связанная сборка, свойству **Копировать локально** которой присвоено значение **true** , копируется в выходной каталог.

## <a name="security-during-the-build-process"></a>Безопасность во время процесса построения
 Visual Studio автоматически настраивает параметры безопасности на компьютере разработчика, чтобы обеспечить предоставление решению доверия во время сборки. Это позволяет решению выполняться во время отладки.

 Проекты Office используют сертификаты для проверки издателя. Visual Studio автоматически создает временный сертификат для идентификации решений Office и настраивает на компьютере разработчика доверие к временному сертификату.

 Дополнительные сведения см. в разделе [решений Office, защита](../vsto/securing-office-solutions.md).

### <a name="network-projects"></a>Сетевые проекты
 Если сборка или документ расположены в сетевой папке, обновления локальной политики безопасности (на уровне пользователя) недостаточно для запуска решения. Администратор должен предоставить полное доверие на уровне компьютера к документам и сборкам, находящимся в сетевой папке, перед запуском решения. Дополнительные сведения о настройке политики безопасности см. в разделе [решений Office, защита](../vsto/securing-office-solutions.md).

 Для проектов уровня документа необходимо также добавить полный путь к расположению документа в список надежных папок Office. Дополнительные сведения см. в разделе [предоставления доверия к документам](../vsto/granting-trust-to-documents.md).

## <a name="change-the-platform-target"></a>Изменение целевой платформы
 Целевой платформой по умолчанию для проектов Office является **Любой ЦП**. Этот параметр обычно не следует изменять. Решения Office, собранные с параметром целевой платформы **Любой ЦП** , выполняются в 32- и 64-разрядных версиях Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] или [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].

 Целевую платформу x64 следует задавать, если вы создаете решение, которое будет выполняться только в 64-разрядных версиях Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] или [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]и вызывать встроенные 64 разрядные интерфейсы API. Дополнительные сведения об изменении целевой платформы см. в разделе [как: Настройка проекта для конкретной платформы](../ide/how-to-configure-projects-to-target-platforms.md).

 Если задана целевая платформа x64, решение не будет запускаться в 32-разрядных версиях Windows или Office. Если в качестве целевой платформы используется процессор x64, решение должно выполняться в 64-разрядном процессе.

## <a name="use-the-clean-command"></a>Использование команды очистки
 Для удаления файлов, созданных при сборке проекта, с компьютера разработчика можно использовать команду **Очистить** в меню **Сборка** среды [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Команда **Очистить** удаляет все файлы в каталоге выходных файлов сборки. Для проектов на уровне приложения команда **Очистить** также удаляет записи реестра, созданные в процессе сборки.

## <a name="related-topics"></a>См. также

|Заголовок|Описание:|
|-----------|-----------------|
|[Отладка проектов Office](../vsto/debugging-office-projects.md)|Описываются проблемы, которые могут возникать при отладке проектов Office.|
|[Пошаговое руководство: Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Содержит сведения о создании базовой настройки на уровне документа для Excel.|
|[Практическое руководство. Повторное включение надстройки VSTO, которая была отключена](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|В этой статье описывается повторное включение надстройки VSTO, которая была оборудования или программного обеспечения отключена.|
|[Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)|Содержит ссылки на сведения о создании решений Office и о роли сборок в решении.|