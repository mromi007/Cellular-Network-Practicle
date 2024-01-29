Hr = 2; % Height of the mobile antenna in meters
f = 2100; % Frequency in MHz
d = 0.5:0.5:15; % Range of Tx-Rx separation distances in Kilometers
Pt = 0.020; % Power transmitted by the BTS antenna in Watts
Gt = 10; % BTS antenna gain in dBi
Ht = 40; % Effective Height of the BTS antenna in meters

% Cell array to store various model names
models = {'Big City (Urban model)', 'Small & Medium City (Urban model); Sub-urban environment', 'Open Rural environment'};
disp('Hata-Okumura Model');
% ... (previous code)

disp(['1 ' models{1}]);
disp(['2 ' models{2}]);
disp(['3 ' models{3}]);
disp(['4 ' models{3}]);

% ... (remaining code)


reply = input('Select Your choice of environment:', 's');

if 0 < str2num(reply) && str2num(reply) < 4
    modelName = models{str2num(reply)};
    disp(['Chosen Model : ' modelName]);
else
    error('Invalid Selection');
end

switch reply
    case '1'
        C = 0;
        if f <= 200
            aHr = 8.29 * (log10(1.54 * Hr))^2 - 1.1;
        else
            aHr = 3.2 * (log10(11.75 * Hr))^2 - 4.97;
        end
    case '2'
        C = 0;
        aHr = (1.1 * log10(f - 0.7) * Hr) - (1.56 * log10(1) - 0.8);
    case '3'
        aHr = (1.1 * log10(f) - 0.7) * Hr - (1.56 * log10(1) - 0.8);
        C = -2 * (log10(f / 28))^2 - 5.4;
    case '4'
        aHr = (1.1 * log10(f) - 0.7) * Hr - (1.56 * log10(f) - 0.8);
        C = -4.78 * (log10(f)^2 + 18.33 * log10(f) - 40.98);
    otherwise
        error('Invalid model selection');
end

A = 69.55 + 26.16 * log10(f) - 13.82 * log10(Ht) - aHr;
B = 44.9 - 6.55 * log10(Ht);
PL = A + B * log10(d) + C;

subplot(2, 1, 1);
plot(d, PL, 'b', 'LineWidth', 2);
title(['Hata-Okumura Path Loss Model for : ' modelName]);
xlabel('Distance - Kilometers');
ylabel('Path Loss (dB)');

% Compute Received Signal Level
Pr = 10 * log10(Pt * 1000) + Gt - PL;

subplot(2, 1, 2);
plot(d, Pr, 'r', 'LineWidth', 2);
title(['Hata-Okumura Model for : ' modelName]);
xlabel('Distance - Kilometers');
ylabel('Received Signal Level (dBm)');
