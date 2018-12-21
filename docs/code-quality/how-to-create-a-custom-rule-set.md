---
title: Создание набора правил анализа пользовательского кода
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 061ceec7a513a0d4c92f06fad5ef730100dbfb8e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000220"
---
# <a name="customize-a-rule-set"></a>Настройка набора правил

Можно создать настраиваемое правило, задать в соответствии с потребностями конкретного проекта для анализа кода.

## <a name="create-a-custom-rule-set"></a>Создание настраиваемого набора правил

Создание набора настраиваемых правил, чтобы открыть встроенный набор правил в **редактор набора правил**. После этого можно добавить или удалить определенные правила, а также можно изменить действие, выполняемое при нарушении правила&mdash;например, отображать предупреждение или ошибку.

1. В **обозревателе решений**, щелкните правой кнопкой мыши проект и выберите **свойства**.

2. На **свойства** страниц, выберите **анализа кода** вкладки.

3. В **выполнить этот набор правил** стрелку раскрывающегося списка, выполните одно из следующих:

   - Выберите набор правил, который требуется настроить.

     \- или -

   - Выберите  **\<Обзор... >** чтобы указать существующий настраиваемый набор правил, если его нет в списке.

4. Выберите **откройте** для отображения правила в редакторе набора правил.

Можно также создать новый файл набора правил из **новый файл** диалоговое окно:

1. Выберите **файл** > **New** > **файл**, или нажмите клавишу **Ctrl**+**N**.

2. В **новый файл** установите флажок **Общие** категории слева, а затем выберите **набор правил анализа кода**.

3. Нажмите кнопку **Открыть**.

   Новый *.ruleset* файл откроется в редакторе набора правил.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Создать пользовательский набор правил в несколько наборов правил

1. В обозревателе решений щелкните правой кнопкой мыши проект и выберите **свойства**.

2. На **свойства** страниц, выберите **анализа кода** вкладки.

3. Выберите  **\<выбрать несколько наборов правил... >** из **выполнить этот набор правил**.

4. В **добавить или удалить наборы правил** диалоговом окне выберите наборы правил, вы хотите включить в новый набор правил.

   ![Добавление или удаление наборов правил-диалоговое окно](media/add-remove-rule-sets.png)

5. Выберите **Сохранить как**, введите имя для *.ruleset* файл, а затем выберите **Сохранить**.

   Новый набор правил, выбранного в **выполнить этот набор правил** списка.

6. Выберите **откройте** Открытие набора правил в редакторе набора правил.

### <a name="rule-precedence"></a>Приоритет правил

- Если же правило перечисленных двух или более раз в набор с разными уровнями серьезности правил, компилятор выдает ошибку. Пример:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Если же правило перечисленных двух или более раз в набор с помощью правил *же* серьезность, может появиться следующее предупреждение в **список ошибок**:

   **CA0063: не удалось загрузить файл набора правил "\[вашей] .ruleset" или один из его зависимых правило файлы набора. Файл не соответствует схеме наборов правил.**

- Если набор правил содержит набор с помощью правил дочерних **Include** тег и наборы правил дочерней и родительской обоих перечислены такие же правила, но с разными уровнями серьезности, то уровень серьезности в родительский набор правил имеет приоритет. Пример:

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>Имя и описание

Чтобы изменить отображаемое имя набора правил, который открыт в редакторе, откройте **свойства** окно, выбрав **представление** > **окно "Свойства"** в строке меню. Введите отображаемое имя в **имя** поле. Можно также ввести описание для набора правил.

## <a name="next-steps"></a>Следующие шаги

Теперь, когда у вас есть набор правил, следующим шагом является настройка правил, добавляя или удаляя правила или изменение серьезность нарушения правил.

> [!div class="nextstepaction"]
> [Изменения правил в редакторе набора правил](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>См. также

- [Практическое руководство. Настройка анализа кода для проекта управляемого кода](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Справочник по набору правил анализа кода](../code-quality/rule-set-reference.md)