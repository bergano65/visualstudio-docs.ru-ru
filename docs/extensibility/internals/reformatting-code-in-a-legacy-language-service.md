---
title: Переформатирование Кодекса в службе языка наследия (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3e83c7299298b16a6fb3178b189479a80e1728
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705912"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Переформатирование кода в языковой службе прежних версий

В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] исходном коде можно переформатировать путем нормализации использования отступов и белого пространства. Это может включать в себя вставку или удаление пробелов или вкладок в начале каждой строки, добавление новых линий между линиями или замену пробелов вкладками или вкладками пробелами.

> [!NOTE]
> Вставка или удаление новых символов может повлиять на маркеры, такие как точки разрыва и закладки, но добавление или удаление пробелов или вкладок не влияет на маркеры.

Пользователи могут начать операцию переформатирования, выбрав в меню **«Предварительный»** **выбор формата** или **формата** из меню **Advanced.** Операция переформатирования также может быть запущена при вставке фрагмента кода или конкретного символа. Например, при вводе закрывающей скобки в C, все между соответствующей открытой скобкой и закрытой скобкой автоматически отступит до надлежащего уровня.

При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отправке команды **«Выбор формата»** или <xref:Microsoft.VisualStudio.Package.ViewFilter> **«Документа формата»** в языковую службу класс вызывает <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> метод в <xref:Microsoft.VisualStudio.Package.Source> классе. Для поддержки форматирования необходимо <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> переопределить метод и предоставить свой собственный код форматирования.

## <a name="enabling-support-for-reformatting"></a>Предоставление поддержки для переформатирования

Для поддержки форматирования `EnableFormatSelection` параметр <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> должен `true` быть установлен при регистрации VSPackage. Это устанавливает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> свойство . `true` Метод <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> возвращает значение этого свойства. Если он возвращается <xref:Microsoft.VisualStudio.Package.ViewFilter> верно, <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>класс вызывает .

## <a name="implementing-reformatting"></a>Реализация реформирования

Чтобы осуществить переформатирование, необходимо извлечь <xref:Microsoft.VisualStudio.Package.Source> класс из класса <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> и переопределить метод. Объект <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> описывает диапазон формата, <xref:Microsoft.VisualStudio.Package.EditArray> и объект содержит в себе вечения, сделанные на пролете. Обратите внимание, что этот диапазон может быть весь документ. Однако, поскольку в диапазоне могут быть внесены несколько изменений, все изменения должны быть обратимыми в одном действии. Для этого оберните все <xref:Microsoft.VisualStudio.Package.CompoundAction> изменения в объект (см. раздел "Использование класса CompoundAction" в этой теме).

### <a name="example"></a>Пример

Следующий пример гарантирует, что есть одно пространство после каждой запятой в выборе, если запятая не сопровождается вкладкой или находится в конце строки. Трейлинговые пробелы после последней запятой в строке удаляются. В этой теме смотрите раздел "Использование класса CompoundAction" в <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> этой теме, чтобы узнать, как этот метод называется методом.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        private void DoFormatting(EditArray mgr, TextSpan span)
        {
            // Make sure there is one space after every comma unless followed
            // by a tab or comma is at end of line.
            IVsTextLines pBuffer = GetTextLines();
            if (pBuffer != null)
            {
                int    startIndex = span.iStartIndex;
                int    endIndex   = 0;
                string line       = "";
                // Loop over all lines in span
                for (int i = span.iStartLine; i <= span.iEndLine; i++)
                {
                    if (i < span.iEndLine)
                    {
                        pBuffer.GetLengthOfLine(i, out endIndex);
                    }
                    else
                    {
                        endIndex = span.iEndIndex;
                    }
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);

                    if (line.Length > 0)
                    {
                        int index = 0;
                        // Loop over all commas in line
                        while ((index = line.IndexOf(',', index)) != -1)
                        {
                            int spaceIndex = index + 1;
                            // Determine how many spaces after comma
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')
                            {
                                ++spaceIndex;
                            }

                            int      spaceCount      = spaceIndex - (index + 1);
                            string   replacementText = " ";
                            bool     fDoEdit         = true;
                            TextSpan editTextSpan    = new TextSpan();

                            editTextSpan.iStartLine  = i;
                            editTextSpan.iEndLine    = i;
                            editTextSpan.iStartIndex = index + 1;

                            if (spaceIndex == line.Length)
                            {
                                if (spaceCount > 0)
                                {
                                    // Delete spaces after a comma at end of line
                                    editTextSpan.iEndIndex = spaceIndex;
                                    replacementText = "";
                                }
                                else
                                {
                                    // Otherwise, do not add spaces if comma is
                                    // at end of line.
                                    fDoEdit = false;
                                }
                            }
                            else if (spaceCount == 0)
                            {
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')
                                {
                                    // Do not insert space if a tab follows
                                    // a comma.
                                    fDoEdit = false;
                                }
                                else
                                {
                                    // No space after comma so add a space.
                                    editTextSpan.iEndIndex = index + 1;
                                }
                            }
                            else if (spaceCount > 1)
                            {
                                // More than one space after comma, replace
                                // with a single space.
                                editTextSpan.iEndIndex = spaceIndex;
                            }
                            else
                            {
                                // Single space after a comma and not at end
                                // of the line, leave it alone.
                                fDoEdit = false;
                            }
                            if (fDoEdit)
                            {
                                // Add edit operation
                                mgr.Add(new EditSpan(editTextSpan, replacementText));
                            }
                            index = spaceIndex;
                        }
                    }
                    startIndex = 0; // All subsequent lines start at 0
                }
                // Apply all edits
                mgr.ApplyEdits();
            }
        }
    }
}
```

## <a name="using-the-compoundaction-class"></a>Использование класса CompoundAction

Все переформатирование, сделанное на разделе кода, должно быть обратимым в одном действии. Это может быть достигнуто <xref:Microsoft.VisualStudio.Package.CompoundAction> с помощью класса. Этот класс заворачивает набор операций редактирования в буфер текста в одну операцию редактирования.

### <a name="example"></a>Пример

Вот пример того, как <xref:Microsoft.VisualStudio.Package.CompoundAction> использовать класс. Пример можно просмотреть в разделе "Реализация поддержки форматирования" в `DoFormatting` этой теме для примера метода.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override void ReformatSpan(EditArray mgr, TextSpan span)
        {
            string description = "Reformat code";
            CompoundAction ca = new CompoundAction(this, description);
            using (ca)
            {
                ca.FlushEditActions();      // Flush any pending edits
                DoFormatting(mgr, span);    // Format the span
            }
        }
    }
}
```

## <a name="see-also"></a>См. также

- [Функции языковой службы прежних версий](legacy-language-service-features1.md)
