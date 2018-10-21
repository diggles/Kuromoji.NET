# Kuromoji.NET

Kuromoji.NET is an Japanese morphological analyzer. This is a pure C# porting of [Kuromoji](https://github.com/atilika/kuromoji).

## Warning

* This is not finished porting everything yet!
* Not compatible original Kuromoji's compiled dictionary, please use this
    * unidic: https://app.box.com/s/tgax5hsj6014g622ymynfz0esq4g8ryo
    * unidic-neologd: https://app.box.com/s/tgax5hsj6014g622ymynfz0esq4g8ryo
    * unidic-kanaaccent: https://app.box.com/s/enwcos5v7gw85angxniwuyqy35bql717

## Usage

```
using Kuromoji.NET.Tokenizers.UniDic;
using System;

namespace Kuromoji.NET.Example
{
    class Program
    {
        static void Main(string[] args)
        {
            var input = "�����i���H�ׂ����B";
            var tokenizer = new Tokenizer(@"path\to\dictionary\unidic.zip");

            Console.WriteLine($"input:\t{input}");
            foreach (var token in tokenizer.Tokenize(input))
            {
                Console.WriteLine($"{token.Surface}\t{token.GetAllFeatures()}");
            }
        }
    }
}
```

output
```
input:  �����i���H�ׂ����B
��      �ړ���,*,*,*,*,*,�I,��,��,�I,��,�I,�a,*,*,���Y,��{�`
���i    ����,���ʖ���,���,*,*,*,�X�V,���i,���i,�X�V,���i,�X�V,�a,�X��,��{�`,*,*
��      ����,�i����,*,*,*,*,�K,��,��,�K,��,�K,�a,*,*,*,*
�H��    ����,���,*,*,����i-�o�s,�A�p�`-���,�^�x��,�H�ׂ�,�H��,�^�x,�H�ׂ�,�^�x��,�a,*,*,*,*
����    ������,*,*,*,������-�^�C,�I�~�`-���,�^�C,����,����,�^�C,����,�^�C,�a,*,*,*,*
�B      �⏕�L��,��_,*,*,*,*,,�B,�B,,�B,,�L��,*,*,*,*
```

## License

* Apache License 2.0

## TODO

* Support ipadic, jumandic, naist-jdic
* Replace double array to [fst](https://github.com/atilika/kuromoji/tree/master/kuromoji-core/src/main/java/com/atilika/kuromoji/fst)