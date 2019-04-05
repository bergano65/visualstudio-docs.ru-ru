---
title: Переформатирование кода в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8b4307caf3f76087867a942654b47bfe85c5011e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979091"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Переформатирование кода в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] исходный код может быть переформатирован, нормализация использование отступов и пробелов. Это могут быть Вставка или удаление пробелы или знаки табуляции в начале каждой строки, добавляя новые между строками или заменив пробелы, символы табуляции или знаки табуляции пробелами.  
  
> [!NOTE]
>  **Примечание** Вставка или удаление символы новой строки могут повлиять на маркеры, такие как точки останова и закладки, но добавление или удаление пробелы или символы табуляции не влияет на маркеры.  
  
 Пользователи могут запускать операцию переформатирования, выбрав **Выбор формата** или **форматировать документ** из **Дополнительно** меню **изменить**меню. Также может запускаться переформатирования операции, при вставке фрагмента кода или определенный символ. Например при вводе закрывающей фигурной скобки в C#, весь код между сопоставления открывающую фигурную скобку и закрывающей фигурной скобки автоматический отступ для правильного выбора уровня.  
  
 При [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отправляет **Выбор формата** или **форматировать документ** команды для службы языка, <xref:Microsoft.VisualStudio.Package.ViewFilter> вызываемый классом <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> метод в <xref:Microsoft.VisualStudio.Package.Source> класса. Для поддержки форматирования, необходимо переопределить <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> метод и задать собственные форматирование кода.  
  
## <a name="enabling-support-for-reformatting"></a>Включение поддержки для переформатирования  
 Для поддержки форматирования, `EnableFormatSelection` параметр <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> должно быть присвоено `true` при регистрации пакета VSPackage. Этот параметр задает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> свойства `true`. <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Метод возвращает значение этого свойства. Если она возвращает значение true, <xref:Microsoft.VisualStudio.Package.ViewFilter> вызываемый классом <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.  
  
## <a name="implementing-reformatting"></a>Реализация переформатирования  
 Чтобы реализовать переформатирования, должен быть производным от класса <xref:Microsoft.VisualStudio.Package.Source> класса и переопределить <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> метод. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Объект описывает диапазон для форматирования и <xref:Microsoft.VisualStudio.Package.EditArray> объект содержит изменения, внесенные в диапазон. Обратите внимание, что этот интервал может быть весь документ. Тем не менее так как вероятно, будет внесение нескольких изменений в диапазон, все изменения должны быть обратимое в рамках одной операции. Чтобы сделать это, заключите все изменения в <xref:Microsoft.VisualStudio.Package.CompoundAction> объекта (см. в разделе «Использование класса CompoundAction» этой статьи).  
  
### <a name="example"></a>Пример  
 В следующем примере проверяется, что имеется один пробел после каждой запятой в выделенном фрагменте, если запятая сопровождается вкладку или в конце строки. Конечные пробелы после удаления последней запятой в строку. См. в разделе «С помощью класса CompoundAction» в этом разделе, чтобы увидеть, как этот метод вызывается из <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> метод.  
  
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
  
## <a name="using-the-compoundaction-class"></a>С помощью класса CompoundAction  
 Все переформатирование сделать часть кода должна существовать возможность отмены, в рамках одной операции. Это можно сделать с помощью <xref:Microsoft.VisualStudio.Package.CompoundAction> класса. Этот класс заключает набор операций редактирования в текстовом буфере, в рамках операции одно изменение.  
  
### <a name="example"></a>Пример  
 Ниже приведен пример использования <xref:Microsoft.VisualStudio.Package.CompoundAction> класса. См. пример в разделе «Реализация поддержки для форматирования» в этом разделе Пример `DoFormatting` метод.  
  
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
 [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)
