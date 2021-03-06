PACKAGE

package shellquote
    import "github.com/samuelbetio/go-shellquote"

    Shellquote provides utilities for joining/splitting strings using sh's
    word-splitting rules.

VARIABLES

var (
    UnterminatedSingleQuoteError = errors.New("Unterminated single-quoted string")
    UnterminatedDoubleQuoteError = errors.New("Unterminated double-quoted string")
    UnterminatedEscapeError      = errors.New("Unterminated backslash-escape")
)


FUNCTIONS

func Join(args ...string) string
    Join quotes each argument and joins them with a space. If passed to
    /bin/sh, the resulting string will be split back into the original
    arguments.

func Split(input string) (words []string, err error)
    Split splits a string according to /bin/sh's word-splitting rules. It
    supports backslash-escapes, single-quotes, and double-quotes. Notably it
    does not support the $'' style of quoting. It also doesn't attempt to
    perform any other sort of expansion, including brace expansion, shell
    expansion, or pathname expansion.

    If the given input has an unterminated quoted string or ends in a
    backslash-escape, one of UnterminatedSingleQuoteError,
    UnterminatedDoubleQuoteError, or UnterminatedEscapeError is returned.


