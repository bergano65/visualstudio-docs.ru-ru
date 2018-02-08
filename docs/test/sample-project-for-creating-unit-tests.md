---
title: "Пример проекта для создания модульных тестов | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b1b92a223a54c48dd08cce2fc02904f1b66606bc
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="sample-project-for-creating-unit-tests"></a>Пример проекта для создания модульных тестов

Этот пример кода предназначен для использования в указанных ниже пошаговых руководствах.

- [Walkthrough: Creating and Running Unit Tests for Managed Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) (Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода). Пошаговое руководство по созданию и настройке модульных тестов, их выполнению и изучению результатов.

- [Пошаговое руководство. Использование служебной программы для тестирования с интерфейсом командной строки](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867). В этом пошаговом руководстве с помощью программы командной строки MSTest.exe выполняются тесты и просматриваются результаты.

## <a name="sample-code"></a>Пример кода

Единственная умышленно допущенная в этом примере ошибка заключается в том, что у метода Debit в m_balance += amount вместо знака плюс перед знаком равно должен стоять минус.

```csharp
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }
    }
}
```

/* Использованные в примерах компании, организации, продукты, доменные имена, адреса электронной почты, эмблемы, имена людей, географические названия и события являются вымышленными. Любые совпадения с реальными именами и названиями случайны. \*/

## <a name="working-with-the-code"></a>Работа с кодом

Для работы с этим кодом необходимо сначала создать для него проект в Visual Studio. Следуйте инструкциям из раздела, посвященного подготовке к выполнению [пошагового руководства по созданию и запуску модульных тестов](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="see-also"></a>См. также

[Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)  
[Пошаговое руководство. Использование служебной программы для тестирования с интерфейсом командной строки](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)
