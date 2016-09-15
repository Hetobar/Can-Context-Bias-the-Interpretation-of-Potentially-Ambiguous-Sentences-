DESCRIPTION

This code is used to perform a self-paced-reading experiment it the platform ibexfarm (http://spellout.net/ibexfarm/ ).
The base of this code is file (example_data.js) from an example experiment.
This specific code is written to perform an experiment, which target is to help me find, if context can influence on understanding of potentially ambiguous sentences.
What exactly is done with this code:
1)Code contains experimental items in form of a list, fillers in form of a list, two practice sentences.
2)Code orders these lists in experimental lists in pseudo-random order.
3)Code initialize other systems of ibexfarm platform, such as form, visualisation and so on.

var shuffleSequence = seq("intro", sepWith("sep", seq("practice", rshuffle("f", rshuffle("s1", "s2", "s3", "s4")))));
This line sets the common order, in which items will be given to participant.

var defaults = [
    "Separator", {
        transfer: 1000,
        normalMessage: "��������� ����������� ����� �������"
    },
    "DashedSentence", {
        mode: "self-paced reading"
    },
    "Question", {
        hasCorrect: false
    },
    "Message", {
        hideProgressBar: true
    },
    "Form", {
        hideProgressBar: true,
        continueOnReturn: true,
        saveReactionTime: true
    }
];
This function defines basic mechanisms of ibexfarm platform

var items = [];
This function contains the body of the programm

    ["intro", "Form", {
        html: { include: "example_intro.html" },
        validators: {
            age: function (s) { if (s.match(/^\d+$/)) return true; else return "Bad value for \u2018age\u2019"; }
        }
    } ],
This block initiates the starting form of self-introduce of the participant.

 ["practice", "DashedSentence", {s: "����� ����� ����� �����, ������ ��� ������. �� ��������� ����� �������."}],
    ["practice", "DashedSentence", {s: "�� ������, � ������ ����� � ������� �� ������. ��� ������� ��� �������� �����, �� ����� � � ��� �����, ��� ��� ����."},
                 "Question", {hasCorrect: false, randomOrder: false,
                              q: "��������� �� � �����������, ��� ����� ����� � ������� � ������?",
                              as: ["��",
                                   "���",
                                  ]}],
This block contains practice sentences

    [["s1",1], "DashedSentence", {s: "1_a ���� �������� �� ����� �����, ����������. ����� ������������ �������� � 9."},
               "Question",       {q: "1_a ���������� �� � �����������, ��� ���� ��������� �����?", as: ["��", "���"]}],
    [["s2",1], "DashedSentence", {s: "1_b ���� �������� �� ����� �����, ����������. Ÿ ����� ��������� � 9."},
               "Question",       {q: "1_b ���������� �� � �����������, ��� ���� ��������� �����?", as: ["��", "���"]}],
    [["s3",1], "DashedSentence", {s: "1_� ���� �������� �� �����, ����� ����������. ����� ������������ �������� � 9."},
               "Question",       {q: "1_� ���������� �� � �����������, ��� ���� ��������� �����?", as: ["��", "���"]}],
    [["s4",1], "DashedSentence", {s: "1_d ���� �������� �� �����, ����� ����������. Ÿ ����� ��������� � 9."},
               "Question",       {q: "1_d ���������� �� � �����������, ��� ���� ��������� �����?", as: ["��", "���"]}],
			   
This block contains all 4 possible variants of experimental items - combination of experimental sentence, contextual sentence, question. 
["sn", m] - this block contains information about sentence-variant number in group("sn", 1<=n<=4) and number of group ("m",1<=m<=32). 
Group number is a number of this experimental item in the whole list of items. Ibex chooses a combination of n and m and orders the item according the Latin square rule. Each "n" is used 8 times for one participant. Each m is used once for one participant.

    ["f", "DashedSentence", {s: "1_f ���� ������� �� ������� ��������, ������ �������� �� ��������. �������� �� ����������, ��� ��� ����� ������ � �������" },
          "Question",       {q: "1_f ���������� �� � �����������, ��� ������ �������� �� �������� ��������?", as: ["��", "���"]}],
		  
This block contains filler items. There are 32 filler item in the list, each of them is used once for one participant.
Each experimental item is followed by filler item.


HOW TO LAUNCH
Ibexfarm gives an opportunity to modify example_data.js and copy the code from inner memory or just edit it in the cloud.
After finishing the edititng code should be saved with a button "save changes" or "save and close". After that the link to the experiment launch will be available.
If there is a mistake in the code, ibex will notice it and show a mistake message, but won't mark, where exactly is a mistake.