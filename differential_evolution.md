# Differential Evolution Algorithm

https://www.cnblogs.com/tsingke/p/5809453.html#:~:text=%E5%B7%AE%E5%88%86%E8%BF%9B%E5%8C%96%E7%AE%97%E6%B3%95%20%28Differential%20Evolution%29%20Differential%20Evolution%EF%BC%88DE%EF%BC%89%E6%98%AF%E7%94%B1Storn%E7%AD%89%E4%BA%BA%E4%BA%8E1995%E5%B9%B4%E6%8F%90%E5%87%BA%E7%9A%84%EF%BC%8C%E5%92%8C%E5%85%B6%E5%AE%83%20%E6%BC%94%E5%8C%96%E7%AE%97%E6%B3%95%20%E4%B8%80%E6%A0%B7%EF%BC%8CDE%E6%98%AF%E4%B8%80%E7%A7%8D%E6%A8%A1%E6%8B%9F%E7%94%9F%E7%89%A9%E8%BF%9B%E5%8C%96%E7%9A%84,%E9%9A%8F%E6%9C%BA%E6%A8%A1%E5%9E%8B%20%EF%BC%8C%E9%80%9A%E8%BF%87%E5%8F%8D%E5%A4%8D%20%E8%BF%AD%E4%BB%A3%20%EF%BC%8C%E4%BD%BF%E5%BE%97%E9%82%A3%E4%BA%9B%E9%80%82%E5%BA%94%E7%8E%AF%E5%A2%83%E7%9A%84%E4%B8%AA%E4%BD%93%E8%A2%AB%E4%BF%9D%E5%AD%98%E4%BA%86%E4%B8%8B%E6%9D%A5%E3%80%82.%20%E4%BD%86%E7%9B%B8%E6%AF%94%E4%BA%8E%E8%BF%9B%E5%8C%96%E7%AE%97%E6%B3%95%EF%BC%8CDE%E4%BF%9D%E7%95%99%E4%BA%86%E5%9F%BA%E4%BA%8E%E7%A7%8D%E7%BE%A4%E7%9A%84%E5%85%A8%E5%B1%80%E6%90%9C%E7%B4%A2%E7%AD%96%E7%95%A5%EF%BC%8C%E9%87%87%E7%94%A8%E5%AE%9E%E6%95%B0%E7%BC%96%E7%A0%81%E3%80%81%E5%9F%BA%E4%BA%8E%E5%B7%AE%E5%88%86%E7%9A%84%E7%AE%80%E5%8D%95%E5%8F%98%E5%BC%82%E6%93%8D%E4%BD%9C%E5%92%8C%E4%B8%80%E5%AF%B9%E4%B8%80%E7%9A%84%E7%AB%9E%E4%BA%89%E7%94%9F%E5%AD%98%E7%AD%96%E7%95%A5%EF%BC%8C%E9%99%8D%E4%BD%8E%E4%BA%86%E9%81%97%E4%BC%A0%E6%93%8D%E4%BD%9C%E7%9A%84%E5%A4%8D%E6%9D%82%E6%80%A7%E3%80%82.%20%E5%90%8C%E6%97%B6%EF%BC%8CDE%E7%89%B9%E6%9C%89%E7%9A%84%E8%AE%B0%E5%BF%86%E8%83%BD%E5%8A%9B%E4%BD%BF%E5%85%B6%E5%8F%AF%E4%BB%A5%E5%8A%A8%E6%80%81%E8%B7%9F%E8%B8%AA%E5%BD%93%E5%89%8D%E7%9A%84%E6%90%9C%E7%B4%A2%E6%83%85%E5%86%B5%EF%BC%8C%E4%BB%A5%E8%B0%83%E6%95%B4%E5%85%B6%E6%90%9C%E7%B4%A2%E7%AD%96%E7%95%A5%EF%BC%8C%E5%85%B7%E6%9C%89%E8%BE%83%E5%BC%BA%E7%9A%84%E5%85%A8%E5%B1%80%E6%94%B6%E6%95%9B%E8%83%BD%E5%8A%9B%E5%92%8C%20%E9%B2%81%E6%A3%92%E6%80%A7%20%EF%BC%8C%E4%B8%94%E4%B8%8D%E9%9C%80%E8%A6%81%E5%80%9F%E5%8A%A9%E9%97%AE%E9%A2%98%E7%9A%84%E7%89%B9%E5%BE%81%E4%BF%A1%E6%81%AF%EF%BC%8C%E9%80%82%E4%BA%8E%E6%B1%82%E8%A7%A3%E4%B8%80%E4%BA%9B%E5%88%A9%E7%94%A8%E5%B8%B8%E8%A7%84%E7%9A%84%E6%95%B0%E5%AD%A6%E8%A7%84%E5%88%92%E6%96%B9%E6%B3%95%E6%89%80%E6%97%A0%E6%B3%95%E6%B1%82%E8%A7%A3%E7%9A%84%E5%A4%8D%E6%9D%82%E7%8E%AF%E5%A2%83%E4%B8%AD%E7%9A%84%E4%BC%98%E5%8C%96%E9%97%AE%E9%A2%98%E3%80%82.


~~~cpp
#include <stdlib.h>
#include <stdio.h>
#include <time.h>
#include <float.h>

double func(double *);
int usage(char *);

// random number generator [0, 1)
#define URAND ((double)rand() / ((double)RAND_MAX + 1.0))

// random number generator initialization
#define INITRAND srand(time(0))

// usage for the program
int usage(char *str) {
    fprintf(stderr, "Usage: %s [-h] [-u] [-s] [-N NP (20*D)] ", str);
    fprintf(stderr, "[-G Gmax (1000)]\n");
    fprintf(stderr, "\t[-C crossover constant, CR (0.9)]\n");
    fprintf(stderr, "\t[-F mutation scaling factor, F (0.9)]\n");
    fprintf(stderr, "\t[-o <outputfile>]\n\n");
    fprintf(stderr, "\t-s does not initialize random number generator\n");
    exit(-1);
}

int main(int argc, char **argv) {
    register int i, j, k, r1, r2, r3, jrand, numofFE = 0;
    extern int D;
    extern double X1[], Xu[];

    int NF = 20 * D, Gmax = 1000, c, index = -1, s = 1;
    double **popul, **next, **ptr, *iptr, *U, CR = 0.9, F = 0.9, min_value = DBL_MAX, totaltime = 0.0;
    char *ofile = NULL;

    FILE *fid;
    clock_t starttime, endtime;

    // Parse command line arguments given by user

    for (i = 1; i < argc; i++) {
        if (argv[i][0] != '-')
            usage(argv[0]);
        c = argv[i][1];
        switch (c) {
            case 'N':
                if (++i >= argc)
                    usage(argv[0]);
                NP = atoi(argv[i]);
                break;
            case 'G':
                if (++i >= argc)
                    usage(argv[0]);
                Gmax = atoi(argv[i]);
                break;
            case 'C':
                if (++i >= argc)
                    usage(argv[0]);
                CR = atof(argv[i]);
                break;
            case 'F':
                if (++i >= argc)
                    usage(argv[0]);
                F = atof(argv[i]);
                break;
            case 'o':
                if (++i >= argc)
                    usage(argv[0]);
                ofile = argv[i];
                break;
            case 's':
                s = 0;
                break;
            case 'h':
            case 'u':
            default:
                usage(argv[0]);
        }
    }

    if (s) INITRAND;

    printf("program parameters: ");
    printf("NP = %d, Gmax = %d, CR = %.2f, F=%.2f\n", NP, Gmax, CR, F);
    printf("Dimension of the problem: %d\n", D);

    // Starting timer
    startime = clock();

    // current generation
    popul = (double **)malloc(NP*sizeof(double *));
    if (popul == NULL) perror("malloc");

    // next generation
    next = (double **)malloc(NP * sizeof(double*));
    if (next = NULL) perror("malloc");

    for (i = 0; i < NP; i++) {
        popul[i] = (double*) malloc((D + 1) * sizeof(double));
        if (popul[i] == NULL) perror("malloc");

        for (j = 0; j < D; j++)
            popul[i][j] = Xl[j] + (Xu[j] - Xl[j]) * UARND;

            popul[i][d] = func(popul[i]);
            numofFE++;

            next[i] = (double *) malloc((D+1) * sizeof(double));
            if (next[i] == NULL) perror("malloc");
    }

}
~~~
