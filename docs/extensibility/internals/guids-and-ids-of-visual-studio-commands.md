---
title: "GUID и идентификаторы команд Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "команды"
  - "id"
  - "размещение команд"
  - "команды Visual studio"
  - "Идентификатор GUID"
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# GUID и идентификаторы команд Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Идентификатор GUID и идентификатор команды, включенных в интегрированной среде разработки \(ide\) Visual Studio определены в файлах .vsct, которые устанавливаются как часть пакета SDK для Visual Studio.  Дополнительные сведения см. в разделе [Команды, определенные в интегрированной среде разработки, меню и групп](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Дополнительные сведения о том, как работать с объектами среды разработки, которые определены в файлах .vsct см. в разделе [Расширение меню и команд](../../extensibility/extending-menus-and-commands.md).  
  
## Найти определение команды  
 Поскольку Visual Studio определяет более тысячу команд, непрактично перечислить все они здесь.  Вместо этого выполните следующие шаги, чтобы найти определение команды.  
  
#### Найти определение команды  
  
1.  В Visual Studio откройте следующие файлы *Путь установки пакета SDK для Visual Studio*\\ \\ VisualStudioIntegration общее \\ Inc \\: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
     Большинство команд Visual Studio определены в SharedCmdDef.vsct и ShellCmdDef.vsct.  VsDbgCmdUsed.vsct определяет команды, которые относятся к отладчику и Venusmenu.vsct определяет команды, которые относятся к разработке в интернете.  
  
2.  Если команда пункт меню, запомните точный текст пункта меню.  Если команда кнопки на панели инструментов, то следует отметить текст подсказки, отображаемый при приостановке.  
  
3.  Нажмите клавишу CTRL\+F, чтобы открыть **Найти** диалоговое окно.  
  
4.  в **Найти** окно, введите текст на диаграмме видно на шаге 2.  
  
5.  Проверьте, то **Все открытые документы** отображает  **Область поиска** окна.  
  
6.  Щелкните **Найти далее** кнопка до текста не выбрана в  `<Strings>` раздел a  [Элемент Button](../../extensibility/button-element.md).  
  
     `<Button>` элемент, команда отображается в определение команды.  
  
 Если был достигнут определение команды можно поместить копию другие команды в меню или на панели инструментов путем создания a [Элемент CommandPlacement](../../extensibility/commandplacement-element.md) то есть эти же  `guid` и  `id` значения в качестве команды.  Дополнительные сведения см. в разделе [Создание многократно используемых групп кнопок](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### Особые случаи  
 В следующих случаях текста меню или текст подсказки не может точно соответствовать, что в определении команды.  
  
-   Пункты меню, включая символ, например подчеркнутый **Печать** команда на  **Файл** меню, в котором p подчеркнутым.  
  
     Символы, предшествуются знака "&" в именах пункта меню отображаются как подчеркнут.  Однако файлы .vsct записываются в формате XML, в котором используется знак "&", чтобы указать, специальные символы и требует амперсандом, который должен отображаться за пределами быть записано как '&amp;'.  Поэтому в файле .vsct, **P**команда rint отображается как '&\#38;amp;Print.  
  
-   Команды, имеющих текст, например динамического **Сохранить** *текущее имя файла*и динамически созданные пункты меню, как элементы  **Последние файлы** список.  
  
     Нет надежный способ найти в динамическом текста.  Вместо этого узлы группа, найдите нужную команду путем обращения к [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) OR  [GUID и идентификаторы панелей инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)и поиск на идентификатор этой группы.  Если определение команды не содержит группу, что сво [Элемент Parent](../../extensibility/parent-element.md)поиск SharedCmdPlace.vsct и ShellCmdPlace.vsct \(или VsDbgCmdPlace.vsct для команд отладчика\), a  `<CommandPlacement>` элемент, который устанавливает родительский объект команды.  SharedCmdPlace.vsct, ShellCmdPlace.vsct, в andVsDbgCmdPlace.vsct *Путь установки пакета SDK для Visual Studio*\\ \\ VisualStudioIntegration общее \\ Inc \\ папка.  
  
## См. также  
 [команды MenuCommand и OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)   
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Справочник по схемам VSCT XML](../../extensibility/vsct-xml-schema-reference.md)