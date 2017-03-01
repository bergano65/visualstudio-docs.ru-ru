---
title: "Форматирование кода в языковую службу для прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 08d537f003279283509913d5f3d6aaa1bb1c4600
ms.openlocfilehash: d78fb976b3500a657d080634c6a041c218c3f1a1
ms.lasthandoff: 02/22/2017

---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Форматирование кода в языковую службу для прежних версий

В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] исходного кода можно изменить с нормализация использование отступов и пробелов. Это могут быть, вставка или удаление пробелов или знаков табуляции в начале каждой строки, добавить новые строки между строками или заменить пробелы вкладки или знаки табуляции пробелами.  
  
>**Примечание:** Вставка или удаление знаков перехода на новую строку может повлиять на маркеры, например точки останова и закладок, но добавление или удаление пробелов или знаков табуляции не влияет на маркеры.  
  
Пользователи могут запускать операцию reformatting, выбрав **Выбор формата** или **документ в формате** из **Дополнительно** меню **изменить** меню. Reformatting операция также может возникнуть при вставке фрагмента кода или конкретный символ. Например при вводе закрывающей фигурной скобки в C# все между сопоставления открывающую фигурную скобку и закрывающей фигурной скобки автоматически отображаются с отступом в правильном режиме.
  
Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отправляет **Выбор формата** или **документ в формате** команду для службы языка, <xref:Microsoft.VisualStudio.Package.ViewFilter>класс вызывает <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>метод в <xref:Microsoft.VisualStudio.Package.Source>класс.</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter> Для обеспечения поддержки форматирования, необходимо переопределить <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>метод и укажите собственный формат кода.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  
  
## <a name="enabling-support-for-reformatting"></a>Включение поддержки для переформатирования  

Для обеспечения поддержки форматирования, `EnableFormatSelection` параметра <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>должно быть присвоено `true` при регистрации VSPackage.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Это задает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>Свойства `true`.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>Метод возвращает значение этого свойства.</xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Если этот метод возвращает значение true, <xref:Microsoft.VisualStudio.Package.ViewFilter>класс вызывает <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter>  
  
## <a name="implementing-reformatting"></a>Реализация переформатирование

Для реализации переформатирование, должен быть производным от класса <xref:Microsoft.VisualStudio.Package.Source>класса и переопределить <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>метод.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Объект, который описывает диапазон для форматирования и <xref:Microsoft.VisualStudio.Package.EditArray>объект содержит изменения, сделанные на диапазоном.</xref:Microsoft.VisualStudio.Package.EditArray> </xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Обратите внимание, что этот интервал может быть весь документ. Тем не менее поскольку скорее всего нескольких изменений в диапазон, все изменения должны быть обратимое в рамках одной операции. Чтобы сделать это, перенос всех изменений в <xref:Microsoft.VisualStudio.Package.CompoundAction>(см. раздел «Использование класса CompoundAction» этого раздела).</xref:Microsoft.VisualStudio.Package.CompoundAction>

### <a name="example"></a>Пример  

Следующий пример гарантирует, что существует одиночный пробел после каждой запятой в выделенном фрагменте, если запятая после чего появится вкладка или находится в конце строки. Конечные пробелы после удаления последней запятой в строку. В разделе «Использование класс CompoundAction» в этом разделе, чтобы увидеть, как этот метод вызывается из <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>метод.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  

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
 
Все переформатирование сделать часть кода должна существовать возможность отмены в рамках одной операции. Это можно сделать с помощью <xref:Microsoft.VisualStudio.Package.CompoundAction>класса.</xref:Microsoft.VisualStudio.Package.CompoundAction> Этот класс инкапсулирует набор операций редактирования в текстовом буфере в эксплуатацию одно изменение.  
  
### <a name="example"></a>Пример

Ниже приведен пример использования <xref:Microsoft.VisualStudio.Package.CompoundAction>класса.</xref:Microsoft.VisualStudio.Package.CompoundAction> См. пример в разделе «Реализация поддержки для форматирования» в этом разделе Пример `DoFormatting` метод.  
  
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

[Компоненты прежних версий языка службы](legacy-language-service-features1.md)
