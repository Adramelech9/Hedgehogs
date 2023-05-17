# Hedgehogs

using System;
using static Hedgehogs.Constants;
public class Hedgehogs {
    public static void Main(string[] args) {
        GetAnswer(SetParameters(args));
    }
    
    private static int[] SetParameters(string[] args) {
        int[] hedgehogs = new int[4];
        string[] input = args[1].Replace("[", "").Replace("]", "").Split(',');
        hedgehogs[3] = int.Parse(args[0]);
        for (int i = 0; i < 3; i++) {
            hedgehogs[i] = int.Parse(input[i]);
        }
        return hedgehogs;
    }
    
    private static bool CanBeChange(int a, int b) {
        return Math.Abs(a - b) == 0 || (a - b) % 3 == 0;
    }
    
    private static void GetAnswer(int[] hedgehogs) {
        int num = 0;
        if (hedgehogs[3] == 0 && CanBeChange(hedgehogs[1], hedgehogs[2]) ||
            hedgehogs[3] == 1 && CanBeChange(hedgehogs[0], hedgehogs[2]) ||
            hedgehogs[3] == 2 && CanBeChange(hedgehogs[0], hedgehogs[1])
        ) {
            switch (hedgehogs[3]) {
                case 0:
                    num = Math.Max(hedgehogs[1], hedgehogs[2]);
                    break;
                 case 1:
                    num = Math.Max(hedgehogs[0], hedgehogs[2]);
                    break;
                case 2:
                    num = Math.Max(hedgehogs[0], hedgehogs[1]);
                    break;
            }
            Console.WriteLine(ANSWER, num);
        }
        else Console.WriteLine(ANSWER, -1);
    }
    
    public static class Constants {
        public const string ANSWER = "minimum number of meetings: {0}";
    }
}

// Online Javascript Editor for free
// Write, Edit and Run your Javascript code using JS Online Compiler

function validSolution(board) {
    for (var i = 0; i < 9; i++) {
        if (board[i].includes(0)) return false;
        
        var uniqueRow = [...new Set(board[i])];
        var uniqueColumn = [...new Set()];
        for (var j = 0; j < 9; j++)
            uniqueColumn += board[j][i];
        if (board[i].length != uniqueRow.length || 
            board[i].length != uniqueColumn.length) return false;
    } 
    return true;
}

var sol1 = validSolution([
    [5, 3, 4, 6, 7, 8, 9, 1, 2],
    [6, 7, 2, 1, 9, 5, 3, 4, 8],
    [1, 9, 8, 3, 4, 2, 5, 6, 7],
    [8, 5, 9, 7, 6, 1, 4, 2, 3],
    [4, 2, 6, 8, 5, 3, 7, 9, 1],
    [7, 1, 3, 9, 2, 4, 8, 5, 6],
    [9, 6, 1, 5, 3, 7, 2, 8, 4],
    [2, 8, 7, 4, 1, 9, 6, 3, 5],
    [3, 4, 5, 2, 8, 6, 1, 7, 9]
])

var sol2 = validSolution([
    [5, 3, 4, 6, 7, 8, 9, 1, 2], 
    [6, 7, 2, 1, 9, 0, 3, 4, 8],
    [1, 0, 0, 3, 4, 2, 5, 6, 0],
    [8, 5, 9, 7, 6, 1, 0, 2, 0],
    [4, 2, 6, 8, 5, 3, 7, 9, 1],
    [7, 1, 3, 9, 2, 4, 8, 5, 6],
    [9, 0, 1, 5, 3, 7, 2, 1, 4],
    [2, 8, 7, 4, 1, 9, 6, 3, 5],
    [3, 0, 0, 4, 8, 1, 1, 7, 9]
])

var sol3 = validSolution([
    [5, 3, 4, 6, 7, 8, 9, 1, 2],
    [5, 7, 2, 1, 9, 5, 3, 4, 8],
    [1, 9, 8, 3, 4, 2, 5, 6, 7],
    [8, 5, 9, 7, 6, 1, 4, 2, 3],
    [4, 2, 6, 8, 5, 3, 7, 9, 1],
    [7, 1, 3, 9, 2, 4, 8, 5, 6],
    [9, 6, 1, 5, 3, 7, 2, 8, 4],
    [2, 8, 7, 4, 1, 9, 6, 3, 5],
    [3, 4, 5, 2, 8, 6, 1, 7, 9]
])
console.log(sol1, sol2, sol3)
