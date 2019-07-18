---
title: Практическое руководство. Устранение неполадок с шаблонами | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 246ce82eef63559060c9c4ea4daabd3ae1e5a284
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435126"
---
# <a name="how-to-troubleshoot-templates"></a>Практическое руководство. Устранение неполадок с шаблонами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если шаблон не загружается в среде разработки, локализовать проблему можно несколькими способами.  
  
## <a name="validating-the-vstemplate-file"></a>Проверка файла VSTEMPLATE  
 Если файл VSTEMPLATE в шаблоне не соответствует схеме шаблона [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], шаблон может не появиться в диалоговом окне **Новый проект**.  
  
#### <a name="to-validate-the-vstemplate-file"></a>Процедура проверки файла VSTEMPLATE  
  
1. Найдите ZIP-файл, содержащий шаблон.  
  
2. Извлеките ZIP-файл.  
  
3. В меню **Файл** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] выберите пункт **Открыть** и затем пункт **Файл**.  
  
4. Выберите файл VSTEMPLATE для шаблона и нажмите кнопку **Открыть**.  
  
5. Убедитесь, что XML-код в файле VSTEMPLATE соответствует схеме шаблона [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения о схеме VSTEMPLATE см. в разделе [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
    > [!NOTE]
    > Чтобы обеспечить поддержку IntelliSense во время работы с файлом VSTEMPLATE, добавьте атрибут `xmlns` в элемент `VSTemplate` и присвойте ему значение http://schemas.microsoft.com/developer/vstemplate/2005.  
  
6. Сохраните VSTEMPLATE-файл и закройте его.  
  
7. Выберите включенные в шаблон файлы, щелкните правой кнопкой мыши, выберите пункт **Отправить**, а затем пункт **Сжатая ZIP-папка**. Выбранные файлы будут сжаты в ZIP-файл.  
  
8. Поместите новый ZIP-файл в тот же каталог, где находится старый ZIP-файл.  
  
9. Удалите извлеченные файлы шаблона и ZIP-файл старого шаблона.  
  
## <a name="monitoring-the-event-log"></a>Мониторинг журнала событий  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] регистрирует ошибки, обнаруженные при обработке ZIP-файлов шаблона. Если шаблон не отображается должным образом в диалоговом окне **Новый проект**, вы можете воспользоваться **средством просмотра событий** для устранения неполадки.  
  
#### <a name="to-locate-template-errors-in-event-viewer"></a>Поиск ошибок шаблона в средстве просмотра событий  
  
1. В Windows нажмите кнопку **Пуск**, выберите **Панель управления**, дважды щелкните **Администрирование** и **Просмотр событий**.  
  
2. В левой области щелкните **Приложение**.  
  
3. Найдите события, у которых `Visual Studio - VsTemplate` имеет значение **Source**.  
  
4. Дважды щелкните событие шаблона, чтобы просмотреть ошибку.  
  
## <a name="see-also"></a>См. также  
 [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
