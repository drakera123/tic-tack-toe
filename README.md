# tic-tack-toe
a code that allows the user to play tick tac toe against a bot
;; These are the opponent identifiers
(setf *opponent1* 10)
(setf *opponent2* 1)

;; This is a list representing the 3 in a row positions on a board that are
;; consider wining rows
(setf *triplets*
  '((1 2 3) (4 5 6) (7 8 9)
    (1 4 7) (2 5 8) (3 6 9)
    (1 5 9) (3 5 7)))

;; If we want random to actually return random numbers that are (a lot less)
;; predictable then we need to seed the random state
(setf *random-state* (make-random-state t))

;; Setup the playing board filled with zeros to start. The playing board will be
;; filled with the *opponent1* and *opponent2* constants as the game progresses.
;; We can use these values to determine which player has won the game
(defun make-board ()
  (list 'board 0 0 0 0 0 0 0 0 0))

;; Print out a ASCII representation of the game board
(defun print-board (board)
  (let* ((convert-to-letter (lambda (v)
          (cond ((equal v 1) "O")
                ((equal v 10) "X")
                (T " "))))
        (print-row (lambda (x y z)
          (format t "~&  ~A | ~A | ~A"
          (funcall convert-to-letter x)
          (funcall convert-to-letter y)
          (funcall convert-to-letter z)))))

  (format T "~%")
  (funcall print-row (nth 1 board) (nth 2 board) (nth 3 board))
  (format T "~& -----------")
  (funcall print-row (nth 4 board) (nth 5 board) (nth 6 board))
  (format T "~& -----------")
  (funcall print-row (nth 7 board) (nth 8 board) (nth 9 board))
